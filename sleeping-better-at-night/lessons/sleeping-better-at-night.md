Tomasz Łakomy: [00:00] Welcome, everybody. Good morning. Good evening. I don't know what time it is in your time zone. In my time zone it's actually 8:00 PM, so it's not yet time for a nap. If you feel like you would like to take a nap, this is absolutely fine.

[00:14] This talk is quite literally about sleeping, so I won't mind because honestly, I can't see you. This is very challenging for me as a speaker because I can't see my audience, but I can see being in the chat.

[00:27] Speaking of audience, I would like to start this talk by addressing the most important person in the room. That person is not me, even though I will be speaking for the next 40 minutes. That person is you. You are the most important ones because there's only one of me and from what I can see, there's over 100 of you.

[00:48] So, I think this makes more sense to focus on the majority instead of this one dude, not on stage, but sitting in his apartment like a loner. I have a question for you, and the question is: why are you afraid of pushing stuff to production on Friday?

[01:09] Why is that, honestly? What's the problem with pushing to prod on Friday? What's the difference between Tuesdays and Friday when it comes to production releases? In theory, there's none because your code probably doesn't care about the day of the week, but there is some. At least we feel like it.

[01:27] And, there is this ongoing debate going on Twitter and other social media about whether you should push to production on Friday in the first place. There are voices in the community, like Kelly (@kvlly on Twitter). Kelly is saying don't push to prod on Friday. It's absolutely not worth it.

[01:44] There's this dude (@tlakomy, the speaker himself) who's saying that it's Friday, YOLO, push to prod, break the world, I don't care. Further, do not sue me if you push to prod on Friday and something is broken. Who is right here? I don't know. I have absolutely no idea.

[02:01] What I did, I reached out to a team of elite scientists from Poland because I'm Polish. This is what they came up with. According to this expert research, if you push to production on Friday, you are 120 percent likely that you are going to break production. This is not true. It's actually a lot higher. It's like 200 percent.

[02:21] Honestly, this is what we feel. This is what we experience. This is what I've been experiencing for the last eight years a front-end developer. I think it's a good time to talk about testing for the next 40 minutes or so.

[02:35] My name is Tomasz Łakomy. I'm a senior front-end engineer at OLX Group. We are the biggest online company that honestly nobody of you has probably heard of. Maybe if you're from Europe, but if you are from the US, probably not so much.

[02:50] I'm also an egghead.io instructor. I joined the team at the end of 2018, and I've been busy. I've recorded 100 Egghead lessons. I've recorded a React 360 course. I'm currently working on the next course on AWS. This is a very exciting time for me, and I'm very happy to be here giving my very first remote talk for the egghead.io community.

[03:14] The reason why I mentioned where I work as my day job is that we are working on OLX Poland. If you are from the US, you are probably familiar with Craigslist. This is basically the same idea. We are our biggest online marketplace in the entire country. We are the top seventh most visited website in the country. There's a tremendous amount of users.

[03:38] The thing that I was honestly not aware of before I joined the team was that there's also OLX in Romania. There's also OLX in Portugal, OLX in Kazakhstan, and many, many other places. The reason why I'm mentioning all of that is that if we have so many users, if we have so many countries to operate, we are trying to always answer the question, "Does it actually work?"

[04:03] That's our software that we pushed to production, that we deployed for our users to enjoy or at least tolerate. Does it actually work? Before we get to that, I think there's actually a question which is a bit more important, at least for me. The question is, "Why do we care? Why do we care in the first place?"

[04:23] To be fair, if you are a engineer, if you are hired by a company, if you push a bug to production, you're probably going to get paid at the end of the month anyway. If you push 200 bugs to production, maybe not so much, but you know the point. It's not about the money.

[04:39] I like to think it's about something else entirely. I like to think it's about empathy. I like to think that, we as human beings, both do and want to care about others. As the developers, there are multiple groups of people that we should honestly care about.

[04:54] First, there's empathy for users. If you are working on anything that anybody's going to use, you should honestly care about their experience, especially if your website allows other people to make a living. For instance, so they can sell something, they can publish videos like on Egghead, they can publish videos on YouTube, or whatever.

[05:13] You have this tremendous responsibility for your users to provide them with the best user experience you can give them, not to mention that they are literally paying your salary, which is excellent if you think about it.

[05:25] There's also empathy for other team members. I think this is also crucial. Most developers -- shit, I hope -- they are not likely to push something on Sunday when there is nobody around in the office, where there's nobody on-call, there's no tests whatsoever, because we care about other human beings.

[05:46] We care about our beloved team members, and we don't want anybody to have to stay longer because we decided to do a YOLO release in the middle of the night. It's about us. It's also about as human beings because we, as developers, need to feel safe.

[06:02] I personally want to be able to go home, not having to worry about my work because I'm not entirely sure of this thing I pushed to production is actually working or not. I'm not sure. Maybe I will get a phone call at 2:00 AM. I don't want that. I want to feel safe.

[06:17] During this talk, we are going to cover the entire testing spectrum. Many people call it a testing pyramid. Ken. C. Dodds calls it a testing trophy. I prefer to call it a testing spectrum, because I believe there's a spectrum when it comes to tests.

[06:32] There are tests that are very close to the developer and not so much close to the user. There are tests that are very, very close to the user's experience. By the way, I'm using the term testing quite loosely here as we see in the next couple of slides. For me, a form of testing is, for instance, things like Prettier or Linter.

[06:54] Why is Prettier a form of testing? First off, Prettier is fricking amazing. I'm a huge fan of Prettier. The fact that I don't have to bother about formatting and the fact that I am not seeing any more debates in code reviews about formatting, indentation, commas, and whatnot, it makes us more productive.

[07:14] Why I think about Prettier in terms of testing? Because of this nice feedback loop. I save a file. If it's formatted, then it means that the syntax is OK. If it's not formatted, I have a syntax error somewhere, which is this incredible fast feedback loop.

[07:29] This is honestly one of the things I think of when it comes to very close-to-the-developer kind of testing. I'm not going to push something to code review if it cannot be formatted by Prettier.

[07:43] There's also Linters, like TestLint, Eslint, and so on. I think they are also great. I'm not going to go too deep into that, but when it comes to Eslint, don't go too far. This is a quote from the conversation that I actually had with somebody who worked for a different -- luckily -- company.

[08:02] They were not able to push changes to production or to code review because they had to store their imports in alphabetical order. Do you know who cares about that? Your Linter. Do you know who doesn't? Everybody else. I don't think this is a good approach to actually do that. Please don't.

[08:20] Next up, when it comes to testing from the code perspective, we have to address types. Types is one of those topics that is not controversial at all. Everybody has exactly the same opinion about types. Yeah, there are multiple talks that we could honestly talk about types for hours.

[08:39] I personally did C++ before I started doing JavaScript for a living. The thing is that I had some experience with types, and nowadays my opinion about types is as follows. Types are great. TypeScript is fantastic, Flow is fantastic, but even if you have 100 percent type code, you will have bugs.

[09:01] If you think this is not true, think about how much software written in C and C++, which are statically typed languages, they do have some bugs. I did throw out quite a few bugs on my own. Trust me. Types won't secure your code from bugs.

[09:18] Moving on. It is actually not legal, and I've checked that with a lawyer, to do a talk about testing without talking about unit tests. We are going to cover that because, boy, oh boy, I do have my opinions about unit tests. They're fricking amazing. I love unit tests.

[09:36] I'm not going to talk about the difference between unit test and integration tests because, for me, what matters is that they do exist. In my team at work, we have 80 percent test coverage. You know what's funny about software? What's funny about numbers in software? As soon as you figure out a number, like 80 percent, you start to wonder, "Why not 100? Why shouldn't we aim for 100 percent test coverage?"

[10:03] You can do that, and this is what you're going to end up with most of the time. Of course, it works. Now, it's 100 percent, but it's not there. This is a funny image from the Internet, from my Twitter account. You should follow me because I'm always posting things like that, which are objectively funny, all the time, as usual.

[10:23] What I think is more important here is highlighting this difference between 100 percent test coverage and confidence in your software because you might have bugs still. Unit tests, they don't secure against your own misunderstanding of the requirements.

[10:41] If you misunderstood the requirements, you end up writing faulty code, and then you're going to write your unit tests to assert that your code is exactly as broken as you think it was. Do not aim for 100 percent test coverage in my humble opinion. Of course, you can do that, but I do not recommend it personally.

[10:59] If not zero, obviously, if not 100, how much and what do we test? It is tricky, and I don't have an exact answer to that because nobody knows what exactly should you test. My favorite example of trying to figure out what to focus on is amazon.com.

[11:19] On amazon.com, if you scroll down -- this is actually true -- if you go to amazon.com, open up their source, and go to the very bottom, there's an ASCII art of a meowing ducky. This is true. This is in production. To the best of my knowledge, you cannot delete this ducky and push to production at amazon.com. It will not pass the pipeline.

[11:41] This is exactly what you should focus on when it comes to testing, and this is what we are going to talk about for the rest of this talk, how to maintain the ducky.

[11:49] On a more serious note, I'm a huge fan of Kent (C. Dodds), one of the instructors of egghead.io, including many other things that Kent is doing. Kent has this great quote, which I honestly 100 percent agree with. The more your tests resemble the way your software is used, the more confidence they can give you.

[12:11] I think this is absolutely true. The closer you are to your users in terms of testing, the better you are as a developer. Honestly, you can -- wait for it -- sleep better at night.

[12:25] We are going to do a tiny code review. We do have a code of conduct at Egghead, and we are not going to make fun of anybody's code. This is the code that I've personally written. This is absolutely fine because I get to make fun of my own code that I've written I think a year ago.

[12:43] What we have over here is some test for a toggle component. So far, so good. I have a toggle. I'm checking if it exists, and I'm checking if it has a label. That's OK. Next up, not so much. I'm testing whether the toggle has some props, and this is not so good.

[13:04] Users typically don't care about props. They are not aware of props. This is not helping us assert the quality of our software because right now we are basically testing if React works as intended. React has unit tests. We don't have to test React.

[13:19] Next up, we are clicking on the toggle, and we are asserting whether it has a class name `toggly-mc-toggle-face`. Again, users are not typically aware of class names. This is not helping us assert if this toggle is actually not broken for our users.

[13:37] There's also this. I had this issue a while ago. This talk is not React-specific, but I've had tests that were broken because I decided to user React hooks in my codebase. The point here is that the same way that your users are not aware if you're using React, jQuery, Svelte, Vue, Angler, or whatever, the same way your tests should not be aware if you're using hooks, classes, or whatever.

[14:05] You should be able to change the implementation of your component with your tests constantly passing. Your tests should not be aware of the implementation beneath them. This is where Testing Library helps a lot. Testing-library.com is a family of testing libraries that you can use to assert the quality of your software.

[14:25] I do highly recommend that because it is a much better approach to what I just showed you in the last slide. The core idea with Testing Library is that, for instance, in testing-library/react, you don't cooperate. You don't think about class names. You don't think about props.

[14:44] Instead, you are thinking in the dimension of texts, labels, and bottom texts, things that users can see and users can interact with. If they cannot see because they have some sort of visual impairment, they can interact with the alt text on images. This is much better for us because we get to evaluate the user's experience.

[15:09] To be fair, using this approach, you will probably end up writing less tests, but they will be better because you will get more confidence in the quality of your software as a result.

[15:19] If you would like to learn more about this way of writing tests, about this way of asserting your code, I cannot recommend [testingjavascript.com](testingjavascript.com) enough. It's an excellent resource. I recently went through all those videos, and I've learned an awful lot. I do highly, highly recommend [testingjavascript.com](testingjavascript.com) and, honestly, everything that Kent is doing.

[15:40] Let's talk about UI. As front-end UI engineers, developers, you name it, we care strongly about UI. We care strongly about our users being able to use our software. When it comes to users, they typically want two things. They want to, one, be able to use our product to accomplish their goals. Two, they want to be done using your product so they can move on.

[16:04] The example I usually give to address this idea is no one enjoys ordering an Uber. The activity of opening the app, searching for a place, choosing a car, clicking confirm Uber, and paying for the car, this is not fun. This is not something that we typically enjoy.

[16:22] What we enjoy is getting the value out of the app. Our goal as software developers is for us to enable our users to always accomplish their goals, whatever it may be, using our product, using our software.

[16:38] When it comes to your users, they will be on mobile, probably most of the time. This is a graph showing the percentage of mobile device traffic worldwide. As you can see, on mobile is roughly 50 percent. This is excluding tablets. It went down a bit for the last two years.

[16:58] I think it's mostly because of Netflix. I know my wife watches Netflix on smart TV, and I think she's responsible for 30 percent of traffic worldwide because all those shows on Netflix which I don't watch, to be fair.

[17:12] It's difficult to kind of assert the quality of our software on all those different devices because I and many others only have two. I have my laptop and I have my mobile phone. Both of those are a bit stronger and a bit more expensive than the equipment that most of our users have.

[17:33] Ideally, I should have something like this on my desk, which I don't. Probably you don't have it as well. Even if you had all those devices on your desk, testing all of that at the very same time was, historically, incredibly difficult. This is why Sizzy is something that helps us adjust this problem.

[17:54] The core idea of Sizzy is that it is a new browser for developers and designers. What it allows us to do is to see all our website, our product, on multiple different simulated devices at the very same time.

[18:11] To show you an example, I'm going to play a quick video. I'm working on my blog, tlakomy.com, by the way. I can see how it looks on all of those different devices, which I don't own, to be fair. I can switch everything to landscape to assert if it's fine. It looks OK so far. It is a browser, so I'm going to experiment a bit.

[18:32] I'm going to change the title of my blog to this beautiful shade of magenta. Amazing because I'm amazing at design. I'm going to change the title of this blog to something a bit larger for SEO purposes. There you go. It's absolutely terrible, so let me go ahead and remove that. Display, no. There we go. Even worse.

[18:52] I'm going to reload all the devices at the very same time. Afterwards, I would like to get some input from the team. I'm going to enter the photo mode. I'm going to take a photo and get a photo of all those different devices at the very same time. This is huge. It's absolutely amazing in my experience.

[19:14] I am currently doing some rebranding and doing design work. Being able to get one screenshot of all those different devices showing the product that I'm working on and send it to the team, it's incredibly useful. I do strongly recommend that if you are doing any UI work whatsoever because it helps you test your things quite a lot.

[19:35][ let']s move on. Let's talk about end-to-end testing. The thing is that more and more teams are turning towards automation, and for a very good reason. The reason is that -- for the record, controversial slide incoming, just to be clear -- if you take the sum of your development team, which is 20 people, for instance, and your users, then statistically speaking, no one cares about unit tests. Even you don't.

[20:09] Think about it. You care about your own unit tests, but if you want to order a pizza online, and there's five different websites, you are not going to check how many unit tests they have. You are going to check if you can log in, if you can select the pizza, if you can pay for the pizza, if they have pepperoni pizza or whatever.

[20:28] You are not going to care about how many unit tests they have. Again, what we should care about the most as developers is to enable our users to go through the most important flows on our websites at all times because nobody is going to check the login page every single day, manually, at least I hope so.

[20:47] This is why more and more teams are turning towards automation. Automated tests allows us to ensure that those core flows of our application are not broken. This is not a new concept at all. I, personally, as an engineer, I've been a part of multiple engineering teams. In most of those teams, we did attempt automation.

[21:10] The thing is that we encountered stability issues in most of the solutions that we ended up using. I am not going to name any of those tools, because, honestly, I haven't used them in a while. I'm sure they have improved, but I do remember having tests that were failing on Tuesday, passing on Thursday.

[21:28] We had tests that were related to position within Mars and Jupiter, so if those planets aligned, the test would pass. Honestly, it was not fun for anybody involved in that. It added to a complete distrust in those tests. We didn't trust those tests because they were failing all the time.

[21:47] Essentially, we've wasted all those hours because I do strongly believe that if you don't trust your tests, if you don't test the result, it's been to have no test whatsoever, honestly. Then at least you are honest, "I don't know what I'm doing. I'm doing a YOLO release every single time because, well, I don't trust my tests."

[22:07] You should aim definitely to be able to trust your tests. This is where I think that [Cypress](cypress.io)s is doing an amazing job. As they say on their website, and it is written the large font, so you have to believe that, "The Web has evolved, and finally testing has as well."

[22:23] By the way, you probably have noticed, but I'm wearing a Cypress t-shirt. Just to be clear, I am not employed by Cypress. They are not paying me for the support. I've been using Cypress for the last two years as a developer, and I do strongly recommend that. I think it's an absolutely fantastic solution.

[22:45] I am not going to talk about Cypress. Instead, I would like to show you a bit about how Cypress works for the developer's perspective. I'm going to go over here, and this is what we are going to do. Taylor is on the call, and we had a conversation recently about embracing the to-do list. This is exactly what I'm going to do.

[23:07] We are going to test this to-do app. You've probably seen one of those. I can remove an item, add an item. It's nothing overly complicated. Think about it. If this is a mission-critical app, you probably want to ensure that everything is not broken, and we are able to continue using this website.

[23:28] I'm going to go over here. On the left-hand side, there's my Visual Studio code. On the right-hand side, there is the Cypress UI. Right now, I have this extremely complicated test. I'm checking whether true equals true. We can see over here that it is, in fact, true. Woohoo.

[23:46] I'm going to change it to false and save it. You will notice that it's failed because true is not false. Awesome. Let me change it to true. Notice when I save what's going to happen. It's going to start the test automatically in an instant. Cypress maintains this speed when it comes to running your tests.

[24:06] Unless you can achieve test-driven development where you write your end-to-end tests before the actual implementation, and I honestly did that, and it works. It actually works most of the time and allows you to be able to define the behavior of your app.

[24:24] I'm going to click on those buttons in those order, and this is the example. This is the behavior I would like to get. Let me go ahead and actually test something. In order to interact with Cypress, you have to do that for the global `cy` object.

[24:39] I would like to visit my page, and I'm going to go ahead and copy the URL from here. There we go. Right now, I have visited my page inside of the Cypress UI. There are a couple of things here that I would like to show you.

[24:58] First up, and this blew my mind the first time I saw it, this is fully interactive. I can add something over here, remove something, and I'm able to use that. This is highly useful for a developer because sometimes your tests may end up in this weird space.

[25:16] For instance, imagine you work for Twitter, and you are somehow between adding and removing a tweet at the very same time. It's weird, and you want to be able to dig in and see what exactly is going on. You can do that because this, again, is fully interactive.

[25:31] Next up, you can see this log over here. For instance, if I click on the request, I'm able to switch the state of the app before and after the request was sent. It allows me to see how exactly the state of my app changes based on each network request.

[25:51] I don't know about you, but I am a senior developer. That means that I'm using console.log-driven debugging all the time. Cypress does an amazing job at that. If you click on the request and open up the console -- which you can totally do, by the way, because this is just a browser -- in the console, I can see that this request was sent to this URL, `api/todos`, and I have a body with those three to-do items.

[26:16] You can also use the Elements panel from DevTools, as you are used to, in order to see, for instance, that this has a class of todo-lists. Let me go ahead and test something. I would like to assert how many to-do items we have on the list.

[26:39] I'm going to do `cy.get`, and boy, do I get this. This is actually using jQuery under the hood. I am not making this up. This is actually jQuery, and this is why Cypress is so amazing, todo-list li should have length -- let me just move it over here so you can see that. There we go -- of 3.

[27:07] Right now, asserting that this todo-list should have a length of three. Can I go home now? Not really because what if someone were to do this, oops, add a to-do item? If I restart the test, it's going to fail because, as you can see over here, I have four to-do items, and, in my test, I'm expecting three items.

[27:33] What can I do? Hmm. Can I do this? Sure, I can do that, but somebody can add an item. Somebody can remove an item. This is a terrible test. What you would like to achieve instead is to have a consistent state of the app before each test to control the backend. Right now, we are not able to control the backend, and our tests are going to be fragile and brittle.

[28:01] What we do instead is to control the backend. With Cypress, we can totally do that. We are going to control the server. Whenever there's a `get` request to `api/todos`, I'm going to return this response. I am so good at live-coding that I'm going to do it with only one hand. There we go.

[28:26] Right now, whenever there's a...Let me actually fix that. Whenever there's a `get` request to`api/todos`, I would like to return this object. This is going to happen every single time this test is executed. Right now, we are not depending on the state of our database for this test.

[28:46] Of course, you should have some tests that are testing your code against the actual production database, but not every test has to be like that. In my experience, the good proportion between tests that are not hitting your backend and tests that are hitting your backend is about 80 to 20 percent.

[29:05] Moving on. If we want to write a bunch more tests for this component, we probably end up copying and pasting this array all the time. Honestly, we don't want that. What we can use instead is a fixture. Cypress allows us to use fixtures as a JSON file.

[29:25] We can see over here that we have a file, `fixtures/todos.json`. Instead of having this huge array, I can just remove all of that and use `fixture:todos`. Save that, and it's going to work as intended because, in my fixture, I have four items. We can see over here that I still have four expected items.

[29:47] Let me do something else. Let me fail this test. You will notice that it is not going to fail automatically. It's going to wait for a bit. It's going to wait for four seconds. The idea is that, I'm not sure if you've noticed, but some of the Web apps out there are kind of slow sometimes because things happen.

[30:06] Cypress is well aware of that, and it is giving you a benefit of the doubt for you to wait for a bit because something may eventually happen. Maybe those items will eventually be loaded, but not so much because this test is going to fail all the time.

[30:21] I'm going to fix this test. Instead, I'm going to make my app slower. Here the slow todos, I'm going to delay it by five seconds. You have slow backend, and then it's OK. That is something that can basically happen in real life.

[30:39] I would like to ensure that this test is going to be executed only after the request has been returned from the server. We can do that with Cypress. I'm going to set an alias for this request. Henceforth, this request shall be known as `load`.

[30:57] Whenever we start the test, we have to wait for this `load` request to resolve. To recap, over here I'm setting an alias for this request to be known as `load`. I have to wait for this `load` request to resolve before I get to continue with the test.

[31:17] If I save that, it is going to wait for five seconds for this `load` request to resolve. Afterwards, it's going to continue with the test. To be clear, it's not going to wait forever. It's going to wait for, I think, 30 seconds. The idea is that if something is not going to happen in 30 seconds, you probably want to fail the test anyway because it is definitely too long for users.

[31:44] Moving on. You probably end up doing this dance of setting up a server, visiting the home page, setting some rules, some requests, and waiting for some things to resolve, a bunch of times in tests. You probably want to be able to extract it somehow.

[32:01] With Cypress, you can create custom commands. This is a command that we are going to create. It's called `initializeApp`. It allows us to create a server and do all those actions that we have in our original test. I can remove all of that and replace it with `initializeApp` instead.

[32:24] It's going to work as intended. It's going to wait for this request to resolve. Afterward, bang, we have a passing test. Just to be clear, please do not go too far when it comes to those custom actions. I've seen custom actions composed out of custom actions. Trust me, you don't want to debug your tests. You want to debug your code and not to have to debug your tests.

[32:51] Let me show you one more example. Things are not going to be always perfect. This is a test that is going to assert what's going to happen when there's a failed request. Let me save that. What we are going to do, we're going to send a `post` request to `api/todos`. We're going to ensure that the request will be a status `500`, so there's an error in production.

[33:16] I'm going to initialize the app. I'm going to start typing, press enter on the keyboard, wait for the request to resolve. I'm not going to worry that I don't have any more items, and I would like to see the error visible. You know what's the best part about Cypress? I didn't have to read the code.

[33:34] Instead, I can just go over here and scroll over those items. I can see the state of my app changing with each action. This blew my mind the first time I saw it. Honestly, it's just fun to see that. It's fun to explore all those different tests in this UI. I do strongly recommend you give it a shot.

[33:59] My personal opinion about Cypress is that we finally get to test our code and not our patience. It's absolutely amazing. If you'd like to learn more about Cypress, there are two amazing courses on Egghead about Cypress.

[34:14] This is one from Andy Van Slaars, "End-to-End Testing with Cypress." There's also "Test Production Ready Apps with Cypress" by Brett. I do highly recommend both of those courses. They're absolutely amazing.

[34:30] Cypress is fantastic, but it is not a silver bullet. There are things that are very difficult to test with Cypress. Imagine this website, egghead.io. I do strongly recommend this website. I'm going to break website with a single line of CSS. There we go.
[
[34:]48] Cypress is not going to catch that because the thing with Cypress is that Cypress doesn't have eyes. It can only see HTML. It can only see the dom. It cannot see what exactly your app looks like. To give you a better example, imagine this website called eBay.com. The whole business model of eBay is built on trust.

[35:11] The idea is that you trust eBay that if you click on this "Buy it Now" button to buy this overly expensive car, you will get the car. Imagine if the website would look like this. Right now, there is a typo on "Buy it Now" button. I am not going to zoom in, because those things will be difficult to notice.

[35:32] There is a typo, and probably Cypress could catch that. If I were to change the font on this button to Comic Sans, well, maybe not so much. Trust me, your users may notice. They will definitely notice this, if you have broken CSS.

[35:48] What is going to happen right now is that the users will say, "I have to give them this much money and they cannot even style a single button." This is the most important button on this website. What's going to happen now is that the entire user trust is broken, because of a single button. We don't want that.

[36:10] This is where a visual aggression comes in. A visual aggression allows us to validate the visual style, the visual side of things in our app to see what changes are we making to our app from the visual perspective. In essence, we are comparing two images. We are comparing our website before and after the production deployment.

[36:31] To be fair, this is not 100 percent new in terms of a concept. There are some open-source solutions that have been doing that for a bit. One of them is BackstopJS, but it does have some issues when it comes to fonts, for instance, because if you run your tests on Linux and your users are using MacBooks, there might be some slight differences in fonts and you may get some false alarms.

[36:53] I've been exploring this earlier, and I've noticed this company called AppliTools. The core idea is that because it is 2020, they do AI-powered visual testing and monitoring. What they do is that they provide you with an SDK for Cypress, for Selenium, and many other testing solutions.

[37:12] You can write your test, open the eyes, basically create a DOM snapshot of your UI, send it over to their cloud. They're going to generate screenshots from those snapshots, and they're going to use AI and a bunch of things that I don't understand in order to validate those DOM snapshots in the cloud.

[37:30] Consider this login form. So far, so good. It's just a typical login form. In order to test this with Cypress, because I took a part in an AppliTools hackathon a while ago, this is the amount of code I ended up writing for those tests.

[37:46] This is the amount of code I ended up writing for AppliTools. Basically, I visit the URL, I open the eyes in order to create the DOM snapshot, check the window, and run eyes closed in order to send this snapshot to AppliTools cloud.

[38:02] This is what it looks like in the UI. You can see the state of the app beforehand, because right now, I don't have any changes. Right now, I do have some changes. Again, those things are difficult to notice.

[38:17] First off, we change the username text to login. That was actually by design. There is a typo in the placeholder. You are not going to notice that. And also Remember Me has been shifted to the right.

[38:32] What's funny about human minds is that as a developer working for this fictional website, you will probably end up seeing this login form hundreds of times a day. Sometimes, it's very difficult to notice those changes, even though you see this page all the freaking time.

[38:49] AppliTools can see that and AppliTools can notice that. It's going to mark you the regions that were actually modified and changed in your tests, and you can mark those some regions as errors, and you can mark some regions as changes by design. You will not pass your tests until you adjust all those things.

[39:08] There's also one more thing is that allow you to do a root cause analysis. If you change, for instance, a placeholder, it's going to tell you exactly what did you change and where, and because of what those tests are failing.

[39:22] If you would like to learn a bit more about AppliTools and visual aggression, there's amazing talk from Angie Jones which is called Your Tests Lack Vision. I do highly recommend that. It's an excellent watch. Please, do watch it after I'm finished talking.

[39:38] There's one more thing. There's one more ultimate form of testing, which I feel that we are not talking enough about. This ultimate form of testing is talking to your users. I cannot emphasize how important this is.

[39:57] At work, we have an integration and user experience laboratory. The core idea is that we invite our users to our office. We have two rooms with this mirror between them. We can see them. They cannot see us, and they can see and interact with our software.

[40:18] Trust me, you can have the micro-est micro-services, the best frameworks, the best CSS-in-JS, GraphQl, whatever. All of this does not matter if users don't care about your software, and they don't want to use it.

[40:34] Honestly, the best and the biggest form of testing is providing the value to your users and asserting if you are providing this value, because this is honestly what we care about as engineers. We want to do our job right. By the way, you don't need a fancy room to do that.

[40:50] There's an amazing book, which is called "Rocket Surgery Made Easy," written by Steve Krug -- it's fairly short, I think it's about 70 pages -- about how can we talk to our users. You can just sit with a user of your own software and just talk to them. You would be surprised by how many things you are going to learn in this very short time, of even like 20 minutes of a discussion.

[41:15] I would like to finish this talk with some key takeaways, so if you literally fell asleep, this is a good time to wake up. First off, care deeply about the user. They are the reason why you are here, and they are the reason why you have a job in the first place. Care about them, care about their experience, and do whatever you can in order to build a better software for them.

[41:38] Closer to user means better tests. Again, the more your tests resemble your software, the way your software is used, the better, and the more confidence they are going to give you. Lastly, and this is the most important one, take care of yourself, honestly, because no matter how many tests you have, things happen. That's OK, that is to be expected. Thank you and goodnight.

Will: [42:08] Thomasz, did you want to field any questions?

Thomasz: [42:11] Yes. By the way, this is the part that people are usually clapping, and I...(laughs)

Thomasz: [42:20] I'm more than happy to answer some questions. Do you want to do those, or should I just watch the chat?

Will: [42:29] I was going to filter through the tray. Rubin said, "Is Cypress any good for Angular unit testing, or should we stick to what Angular provides?"

Thomasz: [42:42] Cypress doesn't care whether you are using Angular or whatnot. What it is going to care about is that if you write basically software in the browser. It's absolutely perfect for Angular, for Vue, or React, whatever.

[42:56] With Cypress you'll click on the buttons, you will write text in form inputs and whatnot. I don't know, for instance, what kind of software they use to build Zoom. I don't care, I know if it's working. It is a perfect solution for Angular and whatever you end up using.

[43:14] There's so many questions, so many comments. By the way, for the record, friends, I'm sorry for not reading the chat during the talk, because I'm not used to that.

Will: [43:23] It's all right.

Thomasz: [43:24] No worries.

Will: [43:25] Frank said, "What do you think about cypress-testing-library commands like FindByText?

Thomasz: [43:32] Sorry?

Will: [43:33] He said, "What do you think about cypress-testing-library commands like FindByText, as an example?"

Thomasz: [43:43] I think it's great. To be fair, I didn't use it very much in production, because for my own personal experience this core Cypress API was enough. I didn't have a feel of embracing this cypress-testing-library, but I've seen some very good feedback about it.

[44:04] The thing is that basically the testing library and family of those libraries, they make it very difficult for you to write bad tests. If you have a feeling that you may have bad testing practices, or maybe your team is just starting with tests, I would say that it's a good idea to embrace that.

[44:25] Because if the API of you library of choice does not allow you to write the bad tests, you are probably not going to write bad tests as a result.

Will: [44:38] Thank you. Daniel, he said, "What are your thoughts on Puppeteer?"

Thomasz: [44:44] Not many. To be fair, you know how when you find someone special, and you don't think about others? This is what happened with me and Cypress.

Thomasz: [44:54] I've heard a lot of good things about Puppeteer, but I'm going to be absolutely honest. I haven't used it in a while, so I don't have very strong opinions on that.

Will: [45:08] Ok, and let's see, Gus said, "Great talk. Where can we see the slides?"

Thomasz: [45:14] I think I have some slides somewhere online, but if I don't, I'm going to post them. By the way, this is my twitter.com (@tlakomy). I'm going to post them there.

Will: [45:34] Kyle, he said, "How may one mock API requests with Cypress if using Fetch in their app?"

Thomasz: [45:45] Could you repeat?

Will: [45:47] Said, "How may one mock API requests with Cypress if using Fetch in their app?"

Thomasz: [45:53] Honestly, the same way that we did during the talk. If you saw, there was this root-call, so basically what the root allows you to do is whenever there's a request to an API originating from your app, you can mock whatever the server's going to return. As a result, you are not going to send the request to the server at all, if I understand the question correctly.

[46:21] I think I've seen Greg on the chat, and Greg is the CTO of Cypress. I think, by the way, folks, if you have any questions for Cypress, also it's a good idea to ping him. They are probably also open to feature requests and whatnot. I think there's actually an answer from Greg in the chat. That's freaking awesome.

Will: [46:44] Cool. Someone said, "Thoughts on a manual testing, and how to balance your test efforts?"

Thomasz: [46:57] That's an excellent question, and I should mention that in the talk, but I didn't. The fact that you embrace automation, and the fact that you are embracing this testing culture as a development team does not mean that you don't have to test your stuff manually.

[47:15] For my money, basically nothing can replace this kind of experience of using the app as a user or, as I mentioned at the end of the talk, just watching other people use it. With automation, your test engineers, your QA department, for instance, they don't have to focus on filling the same form multiple times per week to make sure that you don't have any regression.

[47:39] Instead, they can focus on validating the user experience to checking if it feels good, if it looks good, because those are the things that I won't be able to validate with Cypress.

[47:50] For instance, to give you an example, imagine if you have advertisements on your web page. You may have tests with Cypress that are going to pass 100 percent, but this page is going to be clunky and difficult to use, because advertisements are everywhere, the page is jumping all the time. This is why you need human beings in order to assert that, that everything is fine.

Will: [48:19] I had a question from Marco, and we're probably gonna take like one more after this one. Marco said, "I've had some trouble using Cypress at tests in an app with iframes. Do you have an alternative or a suggestion for that?"

Thomasz: [48:34] Probably Greg is a better person to answer that. I know that it is on their roadmap, and I haven't had a chance to test things that operate within an iframe for a bit. I don't have an experience of that, but I've seen Greg already pasted a link in the chat. By the way, Greg, you should probably do the next one.

Thomasz: [48:56] By the way, thank you, all of you, for joining here today. For me to seeing all those amazing people in the chat and all these questions, it means a lot to me.

Will: [49:10] We definitely do apologize for having the room max out. We definitely didn't anticipate this response, so I definitely really thank everybody for coming through and asking questions and being very active in the chat.

[49:28] We wanted to let everyone know that we are having another one scheduled so far. That will be on Thursday, March 26, at 11:00 AM with Nader. He'll be giving a talk about using serverless in AWS. We'll send out all the stuff out for that soon, but I want to let everyone know where everything is at, and what's coming on next.

[49:55] And if you had anything that you liked, make sure that you talk about it with the hashtag eggheadtalks so you can see who came in, interact with you all. I definitely want to thank everybody like Kernel. I really, really appreciate it, and I'm sure Thomasz does, too. This was really fun.

Thomasz: [50:12] Absolutely.

Will: [50:12] We're looking forward to doing more of these. Everyone, have a good day.

Thomasz: [50:17] Yeah, cheers.
