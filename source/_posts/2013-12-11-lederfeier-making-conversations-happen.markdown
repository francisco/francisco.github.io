---
layout: post
title: "Lederfeier: Making conversations happen"
date: 2013-12-11 12:44:38 -0800
comments: true
categories: TDD RoR WDI-project CoffeeScript Design-Thinking Lederfeier
---

For our second Web Development Immersive project at GA, we were tasked with working with a group of fellow students to build a web app. The first challenge we faced was coming up with an idea. In preparation for that, we decided, as a group, to utilize [design thinking](http://en.wikipedia.org/wiki/Design_thinking) to brainstorm project ideas, and then refine those ideas into something that we would all be proud of at the end of the 8 days allotted to building the app.

The final idea was to build a social party app, which we later called [Lederfeier](http://leder-feier.herokuapp.com) that provided fun prompts to people to spark real-life conversations. While seemingly ironic, we wanted to use smart phones to help people put down their smart phones and have a real conversation! The features were simple: a party planner would be able to create a party, select a prompt rating, and invite participants by entering their phone numbers. Participants could also join by texting a passphrase to a dedicated phone number. Once the party was officially started, all participants would receive a conversation prompt via text message, that they could pass or complete. See below for some prompt examples.

####Prompt Examples:
- Almonds. Discuss.
- If you could make something that's not socially acceptable, acceptable. What would it be?
- Describe the best meal you've ever had
- Describe the characteristics of a perfect pair of socks

Working in a group project was exciting as it allowed each of us to focus on certain parts of the project while learning from eachother's expertise. I've included some thoughts on core aspects of the project below.

####TDD:
To distribute text messages, we used Twilio. The integration was seamless and honestly a charm to put together. However, we quickly realized that testing all the potential participant responses and edge cases via a phone keyboard would be not only expensive (Twilio credits cost money), but VERY time consuming. Fortunately, we made the decision to leverage TDD to test all of the Twilio messages and responses. This decision turned out to be an incredible time saver, and it allowed us to confidently make changes to the app without fear of breaking things.

####Mobile-First and AJAX requests:
To ensure that the user experience was easy to use from a smart phone, we spent a lot of time working on the UI and user flow. We made an effort to minimize user interaction by using ajax requests to refresh page data on a set interval. We also made the buttons big enough to click on from a mobile browser, and only rendered buttons when necessary using jQuery selectors.

####Github: ([Lederfeier Repo](https://github.com/sarlaf/bedazzledbaldachin))
As familiar as we had become with Github during WDI for personal projects, working with Github in a multi-user team presented a new set of challenges. Following best practices, we created a central repo and each team member forked that repo to make changes. Once those changes were ready, a pull request was made and another team member reviewed and accepted the pull request. We quickly learned to rebase off the master on our local forks before sending the pull request to avoid serious version control issues!
