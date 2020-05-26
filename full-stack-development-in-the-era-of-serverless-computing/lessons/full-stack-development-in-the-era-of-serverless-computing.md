Nader Dabit: [0:00] Welcome to Full Stack Development in the Era of Serverless Computing. This talk is going to be maybe the second time I've given this, but I've actually changed a lot. I gave this in Prague, in the Czech Republic, in October, along the same day, actually, I ended up releasing a open source project I'm going to talk about at the end here.

[0:21] You can find me on dev.to, Twitter, and GitHub @dabit3. This is my Twitter avatar. You may have seen me around. I've written a couple of books. I just wrapped up my second book, "Full Stack Serverless."

[0:32] It's actually available to read already on the O'Reilly platform, but you can't buy it yet in paperback. I think it'll be available for sale maybe in like June, July-ish at the earliest and at the latest November.

[0:46] Full Stack Serverless really is more along the lines of what this talk is about. If you're interested in that stuff and you're interested specifically in learning how to do this stuff on AWS, then check out my book. If you're looking to do this stuff, but with some other back end technology, there's a lot of resources out there. I'll talk about some of those at the end of the talk here.

[1:08] The team that I work on at AWS, I've been there for about two years, we are a client technology team. When you think of AWS, most of the time, people think of back end only. They only think of cloud, they think of DevOps. They think of servers, databases, that sort of thing.

[1:25] Our team is actually full of front end engineers as well. We're building stuff for front end and back end engineers, but we're making sure that the stuff that we build is accessible. We actually have a priority on making it accessible and easy to get up and running with for front end developers.

[1:43] We assume that you coming into some of the stuff that we build have never touched AWS before. And we kind of wanted to say, "Oh. You already know JavaScript. You already know how to write command lines from your CLI. You've installed Node, all this stuff." Based on those assumptions, we're going to make it easy to build full stack serverless scalable apps.

[2:06] That's the background on my team. A little background about me is I like the idea of futurism. I think being a futurist has a lot of benefits in your career, or subscribing to the idea of what a futurist is.

[2:22] And Futurism isn't really about predicting the future, actually, even though the name is there. It's more about listening to the current and understanding the implications of what is happening now and how it will affect the future.

[2:40] Then, placing bets in your career, placing bets in different ways, on what the outcome of those things that you're currently thinking about that are happening now. What are the outcomes of these things, like what are the next steps?

[2:57] This is a key part to this talk because I'm going to be making predictions based on actual academic research that I'm going to also lay out here in this talk.

[3:10] What does 'Full Stack' mean? The name of this talk is 'Full Stack Development in the Era of Serverless Computing'. What does 'Full Stack', I guess, in general mean? What does this talk title mean?

[3:26] This is a really interesting quote that I like from Bill Gates. It sums up my philosophy around when I'm learning something, what will I gravitate to? It's typically going to be the thing with the most efficient abstraction. Bill Gates says, "I choose a lazy person to do a hard job because the lazy person will find an easy way to do it."

[3:50] I am not the most academically trained person in the world. I don't have a CS degree. I don't have a master's degree. I think that people like me can find ways to still do good in the world by focusing on the best abstractions and taking hard advantage of those abstractions. I think that's what Bill Gates is saying here. That's again, what the philosophy of this talk is about as well.

[4:15] Abstractions. Let's talk about two portions of abstractions that might be interesting to you if you're watching this talk. You have front end, and you have back end, abstraction. Let's take a look at the front end abstractions and how this has evolved over time.

[4:32] If you were a front end developer 10 years ago, maybe even 5 years ago or even maybe less than that, you could probably get away with knowing HTML, CSS and jQuery. In fact, there are probably people out there writing this stack today getting paid a lot of money to maintain an older project.

[4:48] Of course, there might even be people building new stuff with this stack. It does have its limitations and that's why we've seen the explosion of front end tech.

[4:58] Let's take a look at the new stack. This isn't even everything that is in the new stack. This is a portion of what you might need to learn as a front end developer today. Of course, we still have HTML and CSS. We now have, in addition to that, all of these other things: [JS Frameworks, Webpack, SCSS/CSS in JS, Client Caching, PWA, NPM/Yarn, GraphQL, Unit/E2E Testing, SVG, D3, Redux, Typescript, Git, SSR, Accessibility, Observables, Offline, Responsive Design, JWT].

[5:13] Now, do you have to know all of this stuff to get hired? Probably not, but you probably do need to know quite a bit more than that old stack. If you want to get hired as a front end developer, you more likely than not are going to need to know a JS framework, and JavaScript in general. You're going to need to understand the things around how the built systems work.

[5:36] You might need to understand things like server side rendering. You definitely need to worry about things like accessibility. Depending on the requirements of your app, these things could be interchangeable.

[5:49] This is an assumption like when you're reading a lot of tutorials and stuff today, a lot of these assumptions are made that you know this stuff or maybe they're teaching advanced concepts of this stuff.

[6:02] So, why are we seeing this explosion and complexity on the front end? This is a few different reasons and my opinion why single page applications have become more and more predominantly in the forefront of the newer applications that people are building.

[6:23] When you look at Facebook, you start expecting that user experience as a user. Therefore, what ends up happening is when another company launches an app or a website, they want to provide that same user experience. We're all building based on that top level company that has that really nice, pristine user experience.

[6:48] What ends up happening is those companies are billion-dollar companies, but how can we as smaller companies or medium-sized companies compete with those budgets and things like that. That's again where abstractions come into play.

[7:01] We now have multiple targets. While this isn't a brand new thing, this is definitely becoming more and more of a thing. When I say multiple targets, not only do we have to think about the client side code for a web app, a mobile app, a desktop app and a tablet or whatever, your Apple watch or whatever.

[7:22] You have to also start thinking about how the data access patterns changed not only in the front end, but the back end based on those different targets. For instance, if you're on a mobile phone, your access patterns are going to look a little different on the back end than if you are working with a desktop app.

[7:44] Thinking about this, this become this adds complexity. The data becomes more complex because of those multiple targets basically. Increased user expectations based on the increased user experience provided by competition out there, other apps and other different websites.

[8:02] Microservices are becoming more and more popular leading to more and more endpoints. And because the devices are becoming more powerful, we're able to do more and so we do do more. Then we introduce more of the complexity as the devices become more powerful and we add more stuff. It's this never ending cycle.

[8:24] What are some abstractions though that we're seeing to make this stuff easier? Back in the day when React came out, we used to actually have to open up a webpack config file and write everything from scratch.

[8:35] Now, we have Create React App. That's a really great abstraction that has just and totally boosted productivity and efficiency and the number of people in the React ecosystem. Because now we can run one command line, we have a pretty solid React app ready to roll.

[8:52] All these other things that I've listed here (React Native, NextJS/Gatsby, Style Components, GUIs, Managed GraphQL, Managed Auth) are abstractions that help us overcome some of the things out there. Even with these abstractions, we're still expected to at least fundamentally understand how these things are working under the hood.

[9:07] What about the back end? I'm a front end developer. I'm not a back end developer. I'm becoming more of a back end or full stack developer, but I'm a front end developer. Everything I'm talking about here is new to me in the sense that I haven't really specialized in it, except in the past couple of years.

[9:25] How has back end progressed? Let's take a look at what happened back in the day. If you had a back end system or if you had some back end infrastructure, you typically, back in the day would actually keep it on premise. You would have your server sitting somewhere and you would deal with that.

[9:42] Now, if your house got hit by a tornado or if you had a user access your website from across the world, those were constraints that you had to deal with. For instance, your house gets destroyed, that means your app is down.

[9:57] If someone accesses your site from across the world, there is no caching layer, there is no CDN to deliver that content where that person is. The latency is going to be there. There was a lot of restrictions. Those are just a few of the things that we have with on premise.

[10:13] Cloud is the next step in the evolution of back-end infrastructure. We no longer have to deal with actually the hardware itself but we did still have to deal with scaling, patching, uptime, updating, all that staff. It was more like, "OK, we have this server. It's going to be maintained for us."

[10:31] We might have multiple servers around the world hosting our app but we still have to deal with a lot of shit. A lot of stuff.

[10:41] What came next is what we're currently in the middle of, I would say. It's serverless. Serverless is another layer on top of the Cloud. We now not only have to not deal with all of the actual hardware but we also have additional software obstructions that are helping us out.

[10:59] Scalability would be in my opinion the main one, along with now, instead of paying for the infrastructure itself, you're paying for the compute time that is being used. Those are the two main ones -- the scalability and the dealing with how the payments are concerned.

[11:17] You're no longer paying for the infrastructure, you're only paying for usage. This leads to a lot of things that we're going to talk about. A lot of, I would say, improvements over time. The old way of doing things. Of course, there's no one fit solution, one size fit all but I would say serverless is more and more becoming the better solution.

[11:40] We're going to look at why in detail, why I say that. I like to look past this. In my opinion, the new thing, the current thing is really cool. To me, the coolest thing is what's next. What's after that?

[11:55] This is what excites me because in my career, what has actually helped me set myself aside or a step ahead of some other people that may have not had some of the same equal success that I've had in my careers.

[12:11] I feel in my opinion that I've looked at what the next thing is and jumped on that, and become good at that. That way -- when that time starts turning even more -- that wave there, you're already riding that wave and you're not having to continue to catch up.

[12:25] What is the next thing after serverless? Before we do that, before we talk about that, let's talk about what serverless is in a little more detail.

[12:35] To me, one of the most interesting things that has come out over the last couple of years is this paper that was written by a group at Berkeley. It was called, "Cloud Computing Simplified." This came out last year, in 2019.

[12:50] This is an evolution of another paper they did that was on Cloud Computing. This is the next paper after that, Cloud Computing Simplified.

[13:00] The main thing that I got out of it is this: "While cloud functions -- package as functions as a service offerings -- represent the core of serverless computing, cloud platforms also provides specialized serverless frameworks that cater to specific application requirements as backend as a service offerings."

[13:19] All of that, put at the end, is this. Serverless computing in their opinion is now not just functions as a service but a combination of functions as a service and backend as a service. Backend as a service, like what does that mean? That's things like Firebase or AppSync, the stuff that we're going to talk about.

[13:39] Any managed service, like any service like Algolia, Auth0, all these things in my opinion would be packaged as this backend as a service. Now, when you hear people talk about serverless, they're not only talking about functions as a service, they're more talking about the serverless paradigm.

[13:55] Let's talk about that a little bit more in detail. What are some of the predictions that they make in this paper? This is super interesting to me because I love predictions. First of all, they say in the future we're going to see more backend as a service storage services which has definitely become true.

[14:12] You're seeing things like FaunaDB, you're seeing things like MongoDB has come out with their managed backend as a service. I think we're going to see an explosion of those over the next 10 years. Serverless becomes simpler.

[14:24] This is extremely important because when functions as a service first came out, even now, if you just start getting up and running directly with, for instance, Lambda, Azure, or any of these, that learning curve especially when they first came out was really hard.

[14:42] Now, it's becoming simpler. Now, you're seeing actual companies build things on top of functions as a service cloud providers. Things like Zeit, Netlify, all these other things, Cloudfare Workers, they're basically building...They're using that same thing but they're making it easier and more approachable. That's along the same lines as this. It's going to become easier.

[15:07] Really important piece right here, serverless becomes cheaper than server serverful. This is super important because there are circumstances now where serverful computing is still cheaper than serverless. If you think about it, serverless shines right now in my opinion.

[15:24] If you have either a startup that needs to reduce cost upfront and you want to go ahead and build out a service without spending a ton of money, that's a great use case for serverless. Another one is when you have an inconsistent amount of traffic that's going to be hitting a service.

[15:40] One day you might have zero users, one day you might have a million users. You need to be able to scale up and down without provision being that million users every day. Serverless is perfect for that because you're only going to be paying for the amount that's being used.

[15:54] What they think is in the future that regardless of the service, that serverless will become cheaper regardless. It doesn't matter whether or not you have to worry about provisioning. It's still going to be cheaper.

[16:09] Based on those other predictions, serverful will become less important than serverless. We're going to see this last point shines that takes all these other points and puts into a final statement.

[16:22] Serverless computing becomes the default computing paradigm of the cloud era. When you think of cloud, you're going to now assume that in the future, that serverless is what they're talking about versus vice-versa.

[16:37] Let's take another look at, maybe, a definition of serverless. Ben Kehoe is a great person to follow in the serverless community. He runs engineering teams at iRobot. You may have heard of the Roomba, I think it is, whatever that wireless broom robot that goes around and sweeps up your house. That's iRobot.

[17:05] Anyway, everything they built is serverless. Their big fan is serverless. Ben Kehoe writes a lot of good blog post and thought pieces around this, and talks about how they built their infrastructure architecture in a serverless manner.

[17:21] Instead of saying, whether the definition of serverless is, he has this idea of serverless spectrum. It's more of you have a service or you have a piece of software. It falls on a spectrum of more or less serverless based on a few characteristics versus if it's serverless or not serverless.

[17:43] Instead of saying, "OK, black and white," it's more of like a spectrum or a gray area that falls along these lines. To be more serverless, to follow along the spectrum in a higher manner of serverless, he's saying that it needs to be serviceful plus functions as a service.

[18:02] That's the same thing that Barkley was talking about. Backends as a service or managed services, that's what serviceful means. We'll look a little bit more in depth of what serviceful means in just a moment.

[18:15] A combination of managed services plus functions as a service, a tighter correspondent between resources used and resources built, so paying for what you're using versus paying for what's been provisioned. Then, finally, a smaller and more abstracted control plan.

[18:32] Basically, you have less code to worry about because you're not having to write all of this glue and all of this infrastructure code. You're only writing business logic because you're only having to deal with these serverless functions. Even all of the managed services are off-loading a lot of that code that you would have to write back in the day.

[18:51] What is a serviceful service? A serviceful service inherits all of the things that a serverless function would or the serverless paradigm. No server operations, scale seamlessly, no need to manage uptime, and the variable expense versus fixed expense. Those are more like serverless things.

[19:10] In addition to that, a serviceful service is essentially codeless. If you think of something like Auth0 or Cognito manage all authentication services, these things provide a ton of value. They do a lot of things for you, but you don't have to write any back-end code. It's more of a configuration-based back-end. Then you implement it on the front-end. That's what that is, codeless.

[19:38] Then another definition for a serviceful service or another characteristic, I would say, is that it assumes responsibility for providing a defined set of services. You're subscribing to or you're paying for this set of APIs that they're providing you. You end up saying at the end of the day that that's a good and a bad thing, right?

[20:02] It's good because you have all these things that you can do, but it might be bad because it might limit you on what you can do because you might need something that's out of the current scope of what they offer.

[20:15] What are some examples of these serviceful services? There's just a crazy amount of them, but let's take a look at a few. Cloudinary for dealing with images and stuff, Algolia for search, Auth0 for authentication, Hasura for GraphQL as a service, Netlify hosting functions. They have a lot of other stuff.

[20:39] Even for machine learning and AI, Amazon Rekognition, we support that in Amplify. That is a machine learning service that you don't have to write any code for. You just hit the API with an object describing what you're asking for and what you're sending.

[20:56] For instance, you might send a translation. You might send the text that you want to be translated along with the language code. That would respond with the data back. These are managed services. These are all dealt with for you. They scale it for you. You don't have to deal with anything.

[21:13] Let's talk about the API layer. Of course, everyone probably agrees with this. Data is core to every app. When you're dealing with data, it's really hard to abstract that layer away. How can we do that? In my opinion, right now, if we can get GraphQL into the state that we wanted, this is the best answer that we have and I'll talk about why.

[21:37] One of the main things is that GraphQL offers a menu of what's available. With this menu, you can onboard new developers into your app. You can come back into an old app, see what's going on. You can look at your data graph, and you understand everything that's going on. Let's take a look at another reason using this, why this is important.

[22:00] Microservice architectures are becoming more and more popular. They're becoming more and more widely used in the world. If you look at a lot of these massive companies that have had success, a lot of them are using microservice architectures.

[22:16] What we've done in the past is we typically have an API gateway. In the API gateway, we have these endpoints. Those endpoints would then send a request to whatever services that we have behind there. The problem with this is that your API gateway ends up having a lot of different implementation details that differ across the different services.

[22:37] You might have one endpoint that asks for a certain type of URL. Then the other service is a little different, asking for a different payload. It slows down developer velocity because you end up not having a consistent API endpoints sitting on the back-end.

[22:56] What GraphQL brings to the table is a very consistent API gateway. A GraphQL query is a GraphQL query. A mutation is a mutation. You can't really go outside of the bounds of what the GraphQL implementation is. You end up being able to abstract to weigh your API layer, increasing developer velocity, which is what I'm going to talk about in a moment. It's another core piece to all this.

[23:23] Also, GraphQL offers this idea of schema-centric development. You have your unified data graph. You have just a single entry point. Instead of having all of these different entry points, you have one GraphQL API. You then are just working within the bounds of that schema, working with the mutations, subscriptions, and queries that you defined there.

[23:41] You typically have the front-end and back-end in sync because you know exactly what's available from the back-end by just looking at that schema. You have type safety. You have more simple access to the data that you need per client.

[23:57] For instance, when you're working with all of these different device types -- desktop, mobile, etc. -- being able to ask for only the data you need becomes increasingly important. And GraphQL, it offers that out of the box.

[24:13] Then, finally, you get a consistent API to microservices, name the functions of databases. We could have done this in the past a little bit, but GraphQL brings a more consistent API service to the front-end.

[24:27] With all that in mind, let's talk about this idea of full stack serverless. The name of my book is "Full Stack Serverless." A lot of the stuff I talked about is "full stack serverless." What does this mean? I've defined it as a way of developing with a few different characteristics.

[24:44] Here are the characteristics. Next, I'll talk about the assumptions and acknowledgments. The characteristics are this: you have heavy and intentional use of managed services. You then use serverless functions to fill in the gaps. Whatever you cannot do with a managed service, you can then offload to a serverless function.

[25:04] Then you have your API layer which is, in my opinion, managed GraphQL of some sort. This could be Prisma. It could be Apollo routing in a serverless function. It could be Hasura. It could be even something like FaunaDB with their GraphQL implementation. There's a bunch of things out there.

[25:24] Managed GraphQL would be, in my opinion, more into this characteristic because managed services versus unmanaged. If you're running your own GraphQL server in a serverless function, it's like maybe yes, maybe no. Whatever works for the current constraints of your app would be the main thing to think about.

[25:49] Then, finally, custom client SDKs for API interactions. Why is this important? The paradigm is, in theory, less code is better. When you have client SDKs that abstract the way a lot of the different headers and a lot of the different things that you would have to do just to send a request, that lends itself to less code. That lends itself to more of a serverless approach.

[26:14] What are some assumptions and acknowledgments when you're building apps in this way? First of all, there's a priority of, say, agility is a key market differentiator. When you're building stuff in this day and age, developer velocity will be able to say, "OK, if we have an idea, how fast can we test it out? How fast can we see whether it's working or not and move on to the next idea?"

[26:37] I believe that more experimentation leads to more success. Second of all, code is a liability. We want to have the least amount of code possible. If we can offload something to either a managed service or something that's being made to invite someone else that we trust, then we should do that.

[26:55] The front-end skill set is becoming increasingly valuable, because while we can abstract the way a lot of the back-end services to an extent, the front-end design implementations, taking the data and putting everything together becomes more and more valuable. This isn't something we could easily abstract away.

[27:20] Deliberate focus on not reinventing the wheel. If we can find something that's already been done by someone else that works, then we should lean towards that versus writing it again from scratch.

[27:31] Then what you're starting to see is the idea of a front-end or back-end DevOps/full stack developer. What does it seem to mean anymore? If you, as a front-end developer, can do everything, do you call yourself a full stack developer, or do you call yourself a front-end developer, or a back-end developer, or what?

[27:49] I don't know. To me, it falls into this idea of full stack serverless. What are some benefits of building in this way? Front-end developers move further up the stack naturally. Because you're no longer a front-end developer, you're doing pretty much everything.

[28:05] Increased developer velocity, increased developer efficiency. You're able to do more with less. You're able to experiment. You're able to, in my opinion, be ahead of whatever your competition is if you're able to chop things out with less time, and less effort, and less money. If you're working with these serverless services, again, you're only paying for what's being used.

[28:30] Decreased complexity. By nature, having less code leads to less complexity. This one is really important to me. These types of applications are typically more secure, more reliable, and more scalable.

[28:45] Why is this the case? Think about the people that are building these things. Think about Auth0 for a moment. They've been building one thing for years. 5 years, 10 years, I don't know. They've been doing it for years though and they've been building this one thing.

[29:00] Do you really think that hand-rolling your own service to match the feature set that tens, hundreds, maybe even thousands of engineers have been spending years to build...? That is their core responsibility.

[29:14] Do we really think that rebuilding that thing, ourselves, is going to be more secure and more reliable or scalable? The answer is probably no. Of course, it's not always the case, but typically these types of managed services where you have teams of people spending months and years building something are going to be more reliable because that is their core competency.

[29:34] That's something to take and think about. How can we build applications in this way? When you're talking about this, there's four pieces. You have your managed services. You have your GraphQL. You have your functions. You have your web or mobile framework. That could be client SDKs. That would be nice if you have those. If not, then you're working with the first three.

[30:01] What are some tools that are out there? We're already working with a lot of these. You've seen probably Cloudinary, Auth0, Algolia, Netlify for managed services. Those are different types of managed services.

[30:13] There's a great new serverless GraphQL thing that I've seen, 8base. That's awesome. Hasura is also great. CosmosDB now has implementation. Of course, AppSync. That's what we work on. There's tools out there for this.

[30:28] What I want to talk about is what our team had been working on, specifically for this use case. We were like, "OK, what if we build an entire framework that focus on building everything that we've talked about here but putting it all in one package, and offering everything backed by AWS that which people like Netflix, Airbnb, that have scaled up have already used all these services?

[30:53] What if we were able to package these up and making them accessible, putting them all together?" What Amplify is is what I've been working on, what my team is working on. We have a CLI to create the services. We have the client libraries to interact with them.

[31:07] We have the hosting service to deploy, and then we have a tool chain which is really the CLI-enabling things like GraphQL code generation.

[31:15] Some of the different features that we currently support are authentication, GraphQL APIs, serverless functions and APIs. API getaway with the Lambda function. We have storage for image video, file hosting. We got into machine learning recently. We have hosting, we have analytics. We have a few other categories as well.

[31:35] We support a couple different frameworks. Not only do we support all JavaScript frameworks and Native iOS and Native Android but we have frameworks-specific components. If you're working with React Native, Vue, Angular, or Expo, then you can get up and running with things like authentication with only a couple lines are good.

[31:54] One of the most powerful things that we have in my opinion built into this library is the GraphQL transform library which is a combination of a bunch of different directives that allow you to decorate your GraphQL schema to do a lot of things.

[32:08] For instance, I'm just going to talk about the @model because we're going to get close on time and I'm almost done anyway. For instance, think about when you work with rails and you need to generate a controller and a model for a to do. You might go ahead and generate all that in one command.

[32:26] What you end up getting is a way to create read, update, and delete. You get the UI for that. You get all of these things at once. With GraphQL, there's a common pattern that you typically see. You typically need a GraphQL type. You need operations on that type. So, think about a to do.

[32:44] You might need to create read, update, delete to do queries and mutations, and you might need a subscription for on create, on update or on delete. You might then also need the resolvers that map those operations to your data source, and then you also need your data source.

[33:02] We've taken that into consideration and we've created @model, for instance. You decorate any type with @model. We've create the database, we create all of the additional schema and the resolvers.

[33:12] Using these transforms, you can actually build out an entire back-end by using them and starting declaratively what features that you want. With Amplify, if you want to create a back-end, you just run Amplify init. Amplify add Auth and you're kind of off to the races.

[33:31] A couple of examples of full stack serverless apps that I've build that you can take a look at. Conference App in a Box. This is being used by...So far, I've worked with a little over a hundred conferences that either are going to do it or said they were going to do it. I know that a lot of these events have actually been canceled now so I don't know. laughs

[33:52] I have worked with three consultants that have sold their total, maybe 30 hours of work for over 50 grand because they've been able to get started with this conference out, deploy the back-end.

[34:04] It's a front and a back-end put together. They've billed 50,000 bucks for the project or so, 10, 15, 20 thousand and it's only taken them maybe a few hours to get up and running with. This goes into more of the infrastructure has quote this that I haven't really talked about.

[34:22] Anyway, you end up with a full stack solution that you can package up together when you're using some of our tooling. JamstackCMS is another one. It's a modern take-home WordPress using Gatsby, using serverless tech, and using GraphQL. You can see how it looks here.

[34:41] You can create post, you can create pages. You can have admin features and privileges. You can do themeing. You can do all kinds of stuff. In the build cycle is when we generate the pages using a GraphQL call and the create pages, API in the lifecycle method of Gatsby. So yeah, that's it.

[35:03] What this full stack mean in the era of serverless computing, what is the import of this? This is what I'll end with. The lines are blurred between front-end and full stack development. I think what you're going to see in the future is like everyone is in this era of full stack serverless.

[35:22] Everyone is a full stack developer because once this tooling becomes that accessible, and easy, we're going to stop seeing a differentiator between front and back-end development. I mentioned how the front-end skill set is becoming increasingly valuable. I reiterate that because I think that if you're a front-end developer, you're in a really good place right now.

[35:41] Serverless becomes the default computing platform. GraphQL becomes increasingly important. Something really interesting is this. You're going to start seeing teams organized by feature versus platform or stack.

[35:53] For instance, if you are an engineering team and you need a widget and you're using React Native, you typically used to do, you will need the Native mobile team for iOS to build one, the Native Android team to build one, and the Web team.

[36:12] With React Native, you give that to a single developer, they deploy it across all three platforms. I think you're going to start seeing that in the front-end space or the full stack space.

[36:23] Since that, instead of giving a back-end engineer a feature and then front-end engineer a feature to work together, you'll be able to give a single engineer a feature and they can work across the stack to implement this feature because they're going to understand the full stack.

[36:39] What are the drawbacks here? First of all, you have increased risk when the service is not available and you have no control. If it goes down and it's managed by someone else, you're out of luck. You have a pre-defined feature set that defines the available functionality.

[36:53] If you need something that isn't there, you either have to ask for and wait or you're just out of luck. A lot of these techs are bleeding edge so things change. Then vendor lock-in is definitely one to think about.

[37:06] Because if you're betting on this implementation, if you end up getting 100,000 users, you're locked in at that point and it's hard to move away a lot of times from some of these services.

[37:20] Thank you. That's it. I don't think we have time because we're already over on time. Thank you for coming and listening.
