---
layout: post
title: Essay on greenfield software projects
image: /assets/20210405_header.jpg
description: My personal thoughts on working on greenfield projects. Why do I prefer legacy/mature ones? If you must work on a greenfield then what is it worth to consider?
article_language: en
---

# Are the greenfield projects all sunshine and rainbows?

A couple of weeks ago, we’ve left our previous project. We managed to leave it just after a successful go-live. Thanks to our commitment we delivered it on time. Our company wants to award us for this accomplishment and decided to give us the opportunity to start the new project/product from scratch. We got into a totally new team. Our new team is made of young and dynamic people with an experienced product owner, who understands all the aspects of the agile manifesto. Sounds familiar? 

## Time luxury of a brand new project

We are super excited about the new idea. We are coming up with the name for the initiative, creating a code repository, writing down the coding standards and the definition of done. We’re setting 2 week-long sprints and we create a long backlog of user stories.

### Greenfield software development

In the next weeks, we’re coming up with the abstraction layers to overcome all the issues, that we faced in the previous application when it came to cooperation with the decision-changing customer. We are super proud of 99% of unit tests coverage and continuous deployment applied. Every time we merge something to the master branch, it is getting automatically deployed to the environment! Works like magic.

### Sprint Review goes smooth and gets everyone involved

Every two weeks, we’re doing a sprint review for the product owner and we’re showing all the exciting mechanisms, which will allow us to keep the highest quality of the software. Our UK-based product owner is proud of us and after the sprint review she says “excellent job team”.

## Common pitfalls of greenfield software

After 3 months, we discover that we managed to keep committing the code to the repository but we’re still far from delivering the critical user journey. We were very satisfied with all the tools, that we used and the engineering practices we applied. The codebase got bigger and our test environment was automatically getting the next releases but the sanity testing of the whole system today takes about 2 minutes because the end-user cannot complete the journey to get any value from the solution. The set of the business features is pretty much - limited.

### The new existing code doesn't deliver much value

Based on the UI designs that we’ve got, we implemented all of the features for 3 pages. We even managed to apply a feature flags engine, which will allow our future customer to turn on and off specific features on these pages. The critical user journey still doesn’t work.

### The new existing code cannot be used by a user

Of course, we found a good excuse as to why we were showing just the codebase on a screen-sharing session during the sprint reviews. We were not given important implementation from 3rd party software, which was blocking us from getting the data to fulfill our database with something meaningful, so we couldn’t populate the frontend with any data. The application was not possible to be displayed, nor used.

### First appearance of legacy code

The abstraction layers, that we created required one week of refactoring sprint but finally… we ended up with the possibility for limitless extensions when PO will ask for these.

We cannot understand why the boss of our PO asks about going live the next month. It seems impossible. The label "higher degree of risk"  is being attached to the project. We need to get everyone involved to understand how to rebuild the trust and successfully deliver the solution.

## Customer’s top priorities

People, who drive the business (e.g. sales, operations, c-levels, account managers) tend to value the elements, which directly correspond to one of the following outcomes:

Rising user satisfaction.
* Rising customer satisfaction.
* Rising employee satisfaction.
* These usually lead to rising revenue in a long term. 

### Key success factors of brownfield projects and legacy code

If we think about greenfields in the long term then we need to shift our mindset and learn from past experience. This is where the brownfield projects with good documentation, stable deployment and release strategies, customer support, bug fixing, proper design, and user training usually step in to teach us about the real value.

Usually, people from outside of the scrum team in the customer’s organization tend to value more boring stuff much higher than doing all the greenfield software development activities. Reality shows, that the goals and values of the most newly created scrum/development teams are strongly different from the business ones.

### Speed is valuable, but the long-term quality is a must

For the business people, even at the huge scale companies, when the new opportunity appears they simply want to get it done. If the complex software doesn’t allow them to release the new solution in a matter of days then in many cases they see the simple Zapier integration with Google Spreadsheet as more valuable. After they get the lightweight working solution then they will be super happy about the continuation of this idea by implementing a high-quality system for it.

### Building products with no operational experience

Coming back to the beginning of this article, when we mentioned that our developer managed to leave the project just after going live with it.

The best understanding of the user’s perspective doesn’t come up from participating in 50 projects during the development phase. As long as the project is not being used by real users, we are just making guesses on how our implementation meets the needs.

## Questions to ask when starting a greenfield software project

When working on a new greenfield initiative, that's worth asking the questions:

* How our implementation will help in achieving operational excellence after releasing it to production?
* How are we going to maintain the application and if all of the applied code-level techniques will enable us to keep implementing the new features; or the post-live reality will require us to focus on maintenance in 100%?
* How are we going to release its new versions? Will we be able to deploy every day?
* Will the bug fixing become a pain in the ass? Can we assure relevant stability?
* Will the users like it?
* What would change if instead of being code-focused we would become end-user-focused? It is most likely, that we would get a better understanding of where the money comes from. The software is starting to make the money once it is released to production. Once we understand it, we will come up with the proper perspective on enabling technology. 

## Purpose of the technology and its maintainability

The purpose of technology is “to enable”.

Applying the best engineering practices and keeping the software quality as high as we can are the best steps to reduce the costs in the long term. However, we need to keep in mind that all the practices, which we apply need to come from the needs. Not from our own engineering desires or biases.

Eventually, maybe it will make the decision about staying in the project after going live with it much easier? We will not want to run away from what we’ve created and what we are blaming our decision-changing customers for.

If you’re given the opportunity to maintain and develop the live system then this is the best opportunity to learn a lot about real software development, management, and delivery techniques.

## Iterations and prioritization to the rescue

All the battles around “real Scrum” and “not-by-the-book Scrum” led us to focus on the wrong thing. Mechanics and practices.

Agile Manifesto tells us that our ability to respond to constant changes in close collaboration with our customers is the key. What is missing in it is the end-user and proper understanding of the “working software”.

# Begin with the end in mind 

Even when working on the new software systems before running them live, we may imagine that we already have our end-users and we want to set our highest priority on satisfying them by early and continuous delivery. That means, by applying the proper prioritization, we may implement the critical journey for the specific user persona first. Wrap it with the best engineering practices required for a given phase and then iterate from it.

“Working software” means - really, the working software. Working software means: the end-users may use it to achieve something they need.

## Greenfield software projects - What to keep in mind?

* Set up a test environment as early as possible and share it with your customer. Use it to practice frequent and stable deployments. Think about delivery.
* Focus on defining and delivering the critical user journey first. No bikeshedding.
* No big architecture upfront doesn’t mean no architecture at all. Starting with the code and repository is not always the best first step. A workshop may work.
* People will not understand something just because we give them an explanation. Give the team the questions to answer in the early stages and help them to find the answers by themselves; even if you already know them. Quoting (probably) Alberto Brandolini: “It’s not stakeholder knowledge but developers’ ignorance that gets deployed into production”.
* Communicate the goals and expectations. Make the team understand the business context, not just the descriptions of the Jira tickets.
* Keep codebase quality as high as possible, but do not over-engineer for something that you think will be needed in the future. Quality is the key in long term.
* In most cases, when working in a waterfall-kind-of-project, iterations are the best tool for reducing the project’s risk. The critical aspect here is to remember about the working software, after each iteration.
* Create software that you will want to maintain.
