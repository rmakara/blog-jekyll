---
layout: post
title: Shape Up, Are Pitches the problems to solve?
image: /assets/20220328_header.jpg
description: Shape Up is a product development methodology popularized thanks to Ryan Singer, a Head of Product Strategy at Basecamp. I cover the topics not entirely covered in the book to make your implementation of Shape Up much easier. 
article_language: en
---

> It is one of the articles in the Shape Up series. For Table of Contents go to: [Shape Up, Introduction](https://rmakara.github.io/Shape-Up-Introduction)

In the previous article, we've answered [who does the shaping](https://rmakara.github.io/Shape-Up-Who-does-the-Shaping). Now, let's look at the Pitch and what it contains.

## Pitch structure by the book

Based on the [knowledge from Shape Up book](https://basecamp.com/shapeup/1.5-chapter-06), the Pitch contains:
* Problem 
* Appetite
* Solution 
* Rabbit holes
* No-gos

In this article, I want to explain the model, which may help you decide how concrete the Pitch should be.

## Way how we delegate - matters

A long time ago, someone said that how we describe work to be done matters.

The most modern product management techniques keep saying about giving engineers the problems to solve. It is not a 0-1 game, and not all companies and not all engineers are ready to work in this way. While it might be a good desired state, you may need to start from a different level of work delegation.

Taking inspiration from [7 Levels of Delegation model](https://medium.com/@jurgenappelo/the-7-levels-of-delegation-672ec2a48103), we can imagine a few levels of describing the pitches. On one side, pitches might be micromanaged list of tasks, and on the other side, they may give full autonomy to the Builders.

Let's use the legendary case of eCommerce Cart. Each paragraph below is a separate example.

### L1 - Tech tasks to be done

Please add API methods to enable frontend developers to call it from the UI. The following API interfaces should be:
* addToCart(productId, quantity)
* getCart()
* changeCartItemQuantity(cartItemId, newQuantity)
* removeCartItem(cartItemId)

Remember to include a customer token in a cookie for each endpoint.

Implement the frontend layer to give users the ability to call these API methods. UI layer needs to be implemented based on the designs from Figma.

### L2 - Functional scope to be delivered

Please implement the following actions for the customer:
* Make it possible to add a new item to the cart.
* Make it possible to fetch the current state of the cart.
* Make it possible to change the quantity of an item in the cart.
* Make it possible to remove an item from the cart.

The final solution should contain backend logic and the UI to make it usable for the end-user.

### L3 - Solution to be delivered

Currently, customers of our eCommerce store can purchase only a single item from our catalogue within a single checkout process. We want to let them purchase many items in a single order.

Please implement the eCommerce cart with 4 basic behaviours for adding cart items, fetching the cart, changing quantity and removing an item. Customer needs to be able to proceed to checkout with their cart.

Deliver end to end functionality.

### L4 - Problem to solve

Currently, customers of our eCommerce store can purchase only a single item from our catalogue. Customers can click the "Purchase Now" button on Products Listing Page or Product Details Page and then buy it by going through the checkout page. 

Many of them started asking about having the possibility to buy many items with a single purchase. They want to be able to buy many pieces of the same thing as well as many different items in a single checkout process.

### L5 - Problem to understand and solve

Many of our customers shop about 20 times a day. We sell kitchen furniture in our eCommerce. That's weird. Why do each of them place that many orders to the same delivery address?

### L6 - Problem to discover and solve

Satisfaction analysis of our customers who shop online states the average score is 6 on a scale from 0 to 10. We want to raise their level of satisfaction to 8 during this quarter.

## Which is the best strategy?

All of them are good. Before writing a Pitch, you need to understand the context, which applies just to you and your surroundings.

In not experienced teams delegating concrete tasks to be done may work best. In a super-skilled team, writing down the API methods and classes in a Pitch will make engineers annoyed.

Also, giving problems to solve to the engineering team with no discovery/analysis/experimentation skills might also be risky. Some engineers may not like doing discovery work. The other ones may love it.

## Set the desired state and go for it

In your implementation of Shape Up, you will most likely cooperate with engineers, designers, product managers and other stakeholders to understand the current state and the desired state of how you would like to work.

Based on the results of this assessment, you will be able to choose which strategy to use for writing your pitches.

How you work today in Shape Up is not written in stone. That's going to evolve. Suppose today you describe technical tasks for engineers. In that case, you may agree to reach the level of giving them the whole functional project at the end of this quarter and then continue this journey towards giving them problems to solve at the end of the year.

Even if you reach the highest level of maturity, sometimes you need to get something done. Sometimes you need to experiment with a few solutions for a given problem. Sometimes you need to verify if a problem exists.

## Aren't L4, L5 and L6 a Shaping process?

It looks like they are. 

But once you know the levels of delegating the work, you can try to draw a line between Shaping and Building. Maybe you will include more experimentation into the Building phase for some of the pitches? Or you will not.

## Aren't L1 and L2 a Planning process?

In Shape Up, the projects are given to the teams and then it is up to them how they will plan and execute it. That's true.

We will discuss the Planning process separately in one of the following articles. 

However, as this article is meant to help you understand how detailed the Pitches should be - you need to assess if providing a clear plan to the Builders is a need or not. If you see it as necessary, then I strongly encourage you to start educating the team on analysis, accountability, understanding of the product, planning, work breakdown, and the skill of asking questions.

## From which level shall I start?

If you are just starting with Shape Up, then for most of the teams going with _L3 - Solution to be delivered_ might be a good idea. 

What you are going to do in the next Shape Up cycles will be up to you.

## Disclaimer

Keep in mind, content under the paragraphs above is not an example of the Pitch. It is just an idea of how to describe work to be done.

For some examples of the Pitches go to the official website [Shape Up, Write the Pitch, Examples](https://basecamp.com/shapeup/1.5-chapter-06#examples).
