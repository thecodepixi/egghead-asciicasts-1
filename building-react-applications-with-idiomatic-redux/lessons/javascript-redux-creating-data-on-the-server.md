I added a couple of new functions to the fake API client, in addition to `fetchTodos`, to prepare for this and the next lessons.

The first new fake API endpoint is called `addTodo`. It simulates a network connection, and then it creates a new todo object. It puts the todo with the given text into the `fakeDatabase`, and it returns the `todo` object, just like rest endpoints normally do.

**api/index.js**
```javascript```
export const addTodo = (text) =>
  delay(500).then(() => {
    id: v4(),
    text,
    completed: false,
  };
  fakeDatabase.todos.push(todo);
  return todo;
});
```

The second fake API endpoint I added is called `toggleTodo`. It also simulates a network connection, and it finds the corresponding todo in the `fakeDatabase` and flips its completed field, also returning the `todo` as the response.

**api/index.js**
```javascript```
export const toggleTodo = (id) =>
  delay(500).then(() => {
    const todo = fakeDatabase.todos.find(t => t.id === id);
    todo.completed = !todo.completed;
    return todo;
});
```

In this lesson, we will make the `addTodo` button call the `addTodo` fake API endpoint. I'm opening the file with action creators, I will no longer need the `v4` function because the ID generation now occurs on the server, and instead, I will call the API to add the todo.

**actions/index.js**
```javascript
export const addTodo = (text) => ({
  type: 'ADD_TODO',
  id: v4(),
  text,
});
```

I'm changing the `addTodo` action creator to be a func action creator, so I'm adding `dispatch` as a carried argument. The **func** will call the API `addTodo` endpoint with the given text, and wait for the response to come back.

**actions/index.js**
```javascript
export const addTodo = (text) => (dispatch) => 
  api.addTodo(text).then(response => {

  })
```

When the response is available, it will dispatch an action with the type `ADD_TODO_SUCCESS`, and the server `response`. The newly added todo will be part of the server `response`, so I need to change the `byId` reducer to merge it into the lookup table that it manages.


**actions/index.js**
```javascript
export const addTodo = (text) => (dispatch) => 
  api.addTodo(text).then(response => {
    type: 'ADD_TODO_SUCCESS',
    response,
  });
});
```

I am adding a new case for the `ADD_TODO_SUCCESS` action. I'm using the **object spread operator** to create a new version of the lookup table, where under the `action.response.id` key, there is a new todo object that I read from action response.

**byId.js**
```javascript

const byId = (state = {}, action) => {
  switch (action.type) {
    case 'FETCH_TODOS_SUCCESS': // eslint-disable-line no-case-declarations
      const nextState = { ...state };
      action.response.forEach(todo => {
        nextState[todo.id] = todo;
      });
      return nextState;
    case 'ADD_TODO_SUCCESS':
      return {
        ...state,
        [action.response.id]: action.response,
      };
    default:
      return state;
  }
};
```

If I run the app now and add a todo, it will not appear in the list immediately. I can see the add `ADD_TODO_SUCCESS` in the log, and if I inspect the next state, I will see that the 
byId lookup table now contains all four todos.

![ADD_TODO_SUCCESS console output](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1553542111/transcript-images/javascript-redux-creating-data-on-the-server-output.jpg)

However, we have not updated the `listByFilter`, so all still only has three IDs in the list. If I go to another tab, the new todo appears because its ID is now included in the list of fetched IDs, and similarly, if I go back to the previous tab, it appears now because the data has been re-fetched.

![Output](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1553542110/transcript-images/javascript-redux-creating-data-on-the-server-output2.jpg)

The list of IDs for each tab is managed by a reducer defined inside createList.js. I will change the `ids` reducer to handle the `ADD_TODOS_SUCCESS` action.

When I receive a confirmation that the todo has been added on the server, I can return a new list of IDs with existing IDs in the beginning, and a newly added ID at the very end. Unlike the other actions, `ADD_TODO_SUCCESS` does not have a filter property on the action object, so our initial check would fail.

**createList.js**
```javascript
const createList = (filter) => {
  const ids = (state = [], action) => {
    if (filter !== action.filter) {
      return state;
    }
    switch (action.type) {
      case 'FETCH_TODOS_SUCCESS';
        return action.response.map(todo => todo.id);
      case 'ADD_TODO_SUCCESS':
        return [...state, action.response.id];
      default:
        return state;
    }
  };
};
```

I am removing the top level check, and I will replace it with different checks in different cases. I want to replace the fetched IDs if the filter in the action matches the filter of this list. However, I want the newly added todo to appear in every list except the completed filter, because a newly added todo is not completed.

**createList.js**
```javascript
const createList = (filter) => {
  const ids = (state = [], action) => {
    switch (action.type) {
      case 'FETCH_TODOS_SUCCESS';
        return filter === action.filter ?
          action.response.map(todo => todo.id) :
          state;
      case 'ADD_TODO_SUCCESS':
        return filter !== 'completed' ?
          [...state, action.response.id] :
          state;
      default:
        return state;
    }
  };
};
```

If I run the app now, I can see that if I add a new todo, it appears in the list as soon as add todo success action is dispatched, even though the last time todos were fetched, the new item wasn't there yet.

![Output](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1553542112/transcript-images/javascript-redux-creating-data-on-the-server-output3.jpg)

It will also appear immediately in the active list, before the active todos are even fetched. It will not, however, appear in the completed list because we know that newly added todos are not completed.

If I add a new todo while I'm looking at the completed list, it will not appear there even though the `ADD_TODOS_SUCCESS` action has been dispatched, because new todos are not completed. However, if I switch to active or all, I will see it immediately, even before the corresponding list has been fetched.

Let's recap the changes necessary for adding todo asynchronously. We handle `FETCH_TODOS_SUCCESS` only if the `action.filter` matches the filter that the list was created with, and in this case, we replace the fetched list of todos. Otherwise, we just return the current state.

**createList.js**
```javascript
const createList = (filter) => {
  const ids = (state = [], action) => {
    switch (action.type) {
      case 'FETCH_TODOS_SUCCESS';
        return filter === action.filter ?
          action.response.map(todo => todo.id) :
          state;
```

However, to handle `ADD_TODO_SUCCESS`, we want to check if the filter is not completed, because if we add a todo, it will not be completed, and we want it to appear at the end of the all and the active filter lists.

**createList.js**
```javascript
const createList = (filter) => {
  const ids = (state = [], action) => {
    switch (action.type) {
      case 'FETCH_TODOS_SUCCESS';
        ...
      case 'ADD_TODO_SUCCESS':
        return filter !== 'completed' ?
          [...state, action.response.id] :
          state;
```

I also updated the `byId` reducer that manages the lookup table to handle the `ADD_TODOS_SUCCESS` action. We read the added todo from the `action.response`, and we return a new version of the lookup table that contains it under its ID.

**byId.js**
```javascript

const byId = (state = {}, action) => {
  switch (action.type) {
    case 'FETCH_TODOS_SUCCESS': // eslint-disable-line no-case-declarations
      ...
    case 'ADD_TODO_SUCCESS':
      return {
        ...state,
        [action.response.id]: action.response,
```

Finally, the `addTodo` action creator is no longer synchronous, and instead, it returns a func that calls `addTodo` API endpoint and dispatches an action with the type `ADD_TODO_SUCCESS` and the response from the server.

**actions/index.js**
```javascript
export const addTodo = (text) => (dispatch) => 
  api.addTodo(text).then(response => {
    type: 'ADD_TODO_SUCCESS',
    response,
  });
});
```