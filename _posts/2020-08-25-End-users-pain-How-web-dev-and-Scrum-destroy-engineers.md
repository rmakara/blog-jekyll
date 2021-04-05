---
layout: post
title: End-users' pain. How web dev and Scrum destroy engineers.
image: /assets/20200825_header.jpg
description: My story, on how emotions helped me to be a little bit better engineer. What can we do to bring some of the end-users' pain to our daily life? Is it worth it?
---

# My career's childhood

My engineering childhood was located around many ancient technologies. Before I got into the modern world, my engineering path in 2003 started with writing some C++ code and trainers for Diablo 2. Then I moved on to Webmajster 2, Macromedia Flash, Macromedia Dreamweaver, and mIRC Scripting. After that, when I started my first commercial software engineering job, I had a pleasure working with a super complex system (from the domain perspective) built on top of legacy fundaments in Delphi and PL/SQL.

All of these technologies suffer from similar things, sharing history with Tyrannosaurus, Diplodocus, Triceratops, and other dinosaurs. Technologies mentioned above put me in a much better place in the past than I was in nowadays when I was doing web development as a project manager, product owner, or scrum master.

What's the difference?

The purpose of this article is to leave you with three questions. But first...

# The hype on the user's feedback

When we think about software and product engineering nowadays, we tend to speak a lot about feedback loops. In most cases, Scrum is always around the corner as a 100% receipt for gathering the user's feedback after each Sprint in the form of Sprint Review.

It is not only related to software engineers. I am a guy who likes to visit meetups, which are not related to my core skills. I sometimes go to some UX Design, Business Analyst, Human Resources events, and more. Most of them are somewhere around "We are so cool, meeting end-users' exceptions is what we love! We do everything to respond to the user's feedback, which is the most important aspect of our job!".

And let's get back to mighty Scrum and Sprint Reviews. When we work as web developers, we are most likely to develop some webpage, which will be used by many end-users through the web browser. In a Sprint Review, we usually do not meet with end-users but with business stakeholders. We receive the feedback related to meeting the commitment that we made during Sprint Planning. After the Sprint Review, in the most favourable scenario, we will be able to click the "Approve" button in our continuous delivery process and release the changes to production. Maybe after 1-6 weeks, we will send some surveys to our end-users about their opinion on the changes applied in a production environment. Perhaps we will use some analytics tools, user behavior monitoring tools like HotJar. Maybe we will calculate the average revenue made during the specific time. I do not see the end user's feedback here.

I think when it comes to getting feedback from the end-users. Scrum is the thing, which destroyed the real user feedback. Core agile values and principles were built around the feedback. Scrum was not. The idea that made gathering information from the end-users possible was DevOps. We may do that by raising the frequency of deployments and releases to the production environment and performing A/B tests. It is much closer to collecting the data, which we may interpret as "end-users feedback", than the feedback we get during Sprint Reviews.

Now, let's think about the distance. If you travel from Warsaw, Poland to Wroclaw, Poland then a distance is smaller than when traveling from Warsaw, Poland to Barcelona, Spain.

# Data distance in engineering

There is the following concept - a distance of the data might be a measure of latency. On a hardware level, we may think about using the multi-tier caches (L1, L2, L3...) in a CPU as a closer source of data to the one that we have in RAM, and also when we are accessing the data from HDD/SSD then it is even greater range.

We can expand it even further and think about the Internet. When we access something in LAN, we may get it faster than get it from the server located in some hosting company or cloud provider through WAN. Then we may think about some server located on the other continent and the optical fiber, which go under the ocean. Then we may think about CDN, availability zones, or companies like Akamai.

All of the terms mentioned above are related to - if something is far away from us, we need to wait a little longer to receive it.

The length of the road and its quality - matter. Let's move it on the human level.

# Legacy implementations

In the story about ancient technologies and my first steps in the commercial engineering career path when I worked with Delphi, I worked on ERP and WMS systems. Both systems were using a client-server architecture. There were a few desktop applications and additional devices like handheld warehouse scanners, fiscal printers, and more.

To implement such a system for our customers, we had to travel to some factory located in Europe or China. Talk to the people, look them in the eyes, sit down together at the computer, and teach them how to use the software.

We also had to talk with the people in top company management and teach them how to use reporting. Talk to middle management and show to manage the orders, procurement, inventory fulfilment, supply orders, and customer orders. Also, people in the warehouse, who needed the training to organize the warehouse more efficiently, perform daily work in terms of taking some products from one place to the other in the warehouse (by using muscles!), when to do the scanning etc.

I remember two stories.

# First story - Inventory taking

Story number one is associated with an inventory taking process, that each warehouse had do make just after New Year's Eve.

I was getting drunk at midnight, and the next day on the 1st of January, we were traveling to the customer's warehouse to help employees. I used our software, lifted 20-40 kg products from one place to another, scanning the barcodes. I was even using the handheld scanner 7 meters above the ground, standing on a forklift.

# Second story - Fixing the bug

The second story is about using computers to support people who worked in the warehouse in the same company.

It was 5 pm when a few trucks were waiting for the products to be loaded so that the drivers can start the logistics process and travel to the other country. There were eight warehousemen still at work who wanted to load the trucks as soon as possible, go home, and have fun with friends and family. And also, there was me staying in the warehouse with a notebook placed on the warehouse pallet. I tried to fix a bug, which locked eight people in the warehouse... not only from scanning the barcode, creating an outcome warehouse document, giving it to the truck driver, and loading the truck. The bug was blocking them from going back to home to have fun with their friends. They couldn't leave because the drivers would have to spend an additional night sleeping in the truck to wait for the next day before they could start travelling to another country.

As a result, I stayed with this laptop, having 10+ people around me sniffing behind my neck, and watching me clicking on the keyboard. After many naughty SQL statements on the production database, I ended up saying, "Done. Scan it. Print. Go home". Everyone ended up happy.

# Third story - Using SaaS to run my company

The third story is about me running a little company after hours. I was importing GSM accessories from China and selling them in Poland via Allegro (e-commerce platform). I had 1-2 employees. We were using something called "Sales Manager for Allegro" - a software for improving the process of managing the auctions, sold products, collaboration with postal office, payment gateways, and more.

I was selling about 100~ products a day. Every day, after finishing my software development job at 4 pm, I was going back home, running Sales Manager for Allegro, preparing the stickers, preparing the packages, going to the postal office, and sending it to my customers.

There was an issue with this tool. When I was getting money from my customers through the payment gateways, then sold items were getting flagged with "Paid by payment gateway". Every day, I had to go through 100 rows in the table, tick checkboxes at the rows, which have been paid and move these to the other section. Just to separate paid orders from the ones that haven't been paid yet. After that, I was able to continue with the process of preparing postal stickers and packages.

I asked my friend to help me write a JavaScript code to automate this daily process. The code added just one additional button in Sales Manager for Allegro. Its functionality was "tick all the checkboxes at rows, which have been paid" so I could move these to the other section by doing 2 clicks instead of 102. Every day.

# Feedback distance

The learning from the stories above is - feedback distance. When I was working with Delphi and doing on-site implementations, all of those who were using my code and my software were close enough to hit me in the face because my work had a negative impact on their lives.

When we work in web development, we have a few big firewalls between our users and us. Internet, Sprint Review, Product Owners, Business Stakeholders. In most cases, we never meet our users. In most cases, we do not even use our products, our code.

When we are behind these firewalls, we do not feel end-users pain. We do not look them into the eyes. We do not feel guilty. We do not see how they're losing trust and how it stresses them daily.

> An empowered engineer depends on having a visceral understanding of the customer's pain. Strong engineers hate to see customers that are struggling or unhappy. They take it personally.
>
> -- Marty Cagan

# Sprint Backlog is your enemy

The continuation of that problem is working as a software developer just on the sprint backlog items in Jira. When we do so, we simply focus on delivering the single ticket to the right on the board, so the Development process finishes for us and we can pass it to some Delivery, DevOps, or Operations team.

There is a great quote popularised by Amazon and Atlassian in the past - "you build it, you ship it", which is about taking the total accountability for writing the code, delivering it to the end-users, listening, and proactively asking about their feedback.

Taking ownership of the whole process, All of it by a single developer, who started the journey by assigning himself/herself a Jira ticket.

# Project Manager is not better

When we use project managers as our single point of contact with our clients, stakeholders, who are not our end-users, it may get even worse. We are adding 1 step in the feedback loop. It becomes more like the Chinese Whispers Game (PL: Głuchy Telefon) when the feedback is being modified on each communication stage.

Thanks to many modern concepts like DDD and Event Storming - developers tend to get closer to the business stakeholders and users, which leads to positive impacts on all of us (including project managers).

# Engineer's accountability

I wouldn't like to force anyone to use some specific methods of working. The software engineering world needs the people, who write code, the ones who work with the customers, and the ones who are the mix of both. Everyone is needed in the industry.

The ask here for you is to ask yourself.

__Question 1:__ Which type of engineer you want to be?

All types are worth a lot. All types are needed. All types are essential for our team's joint success, customers, and the software engineering industry.

My concern here is - ask yourself the question, and answer it with self-awareness. Then being conscious - continue going through the path and do your job as you like, to satisfy yourself. To be happy and help others.

# Delphi is better than Cloud-Native

For me, personally. Starting another greenfield web application project, having all of these firewalls, not feeling the daily pain of the people (users, teams, or whoever); focusing on the code instead of the value it delivers and impacts it creates - is not my cup of tea.

Keeping that in mind, working in legacy Delphi code decade ago was more interesting to me than working with cool stuff with scalability, queues, pipelines, monitoring tools, scrums. All of it for the users I will never see.

The problem here is not technology, not a tool. The question that I would like to ask is:

__Question 2:__ What do you do to feel end-users' pain to improve your software products as a development team member?

# My future

The thing that makes me happy today is the possibility of working with the teams and doing my best to make their daily lives better. If I can deliver "the value" to the end-customers by making my team members and colleagues happier and more productive, this is my understanding of the "value," and it is worth my time.

However, maybe it is time to start working on the important stuff, which creates a positive impact on our planet, environment, and human lives? Or maybe start working for the company that produces the product that I use daily? Maybe get back to supporting operations in the non-IT company and grow them by applying technology? Work on companies' digitalization to help all its employees? Or leave the software industry and become a crossfit or water sports coach? Maybe shall I focus 100% on people?

Having broad experience instead of being an expert in a single thing is the root of all evil for me.

__Question 3:__ Where do you imagine yourself in the future?
