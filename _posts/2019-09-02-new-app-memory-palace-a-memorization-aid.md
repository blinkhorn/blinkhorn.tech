---
title: "New App: Memory Palace, a Memorization Aid"
date: "2019-09-02"
categories: 
  - "aws"
  - "blog"
  - "js"
  - "music"
  - "react"
tags: 
  - "ar"
  - "artificial-reality"
  - "express"
  - "express-js"
  - "javascript"
  - "memory-journey"
  - "memory-palace"
  - "mern"
  - "mern-stack"
  - "method-of-loci"
  - "mongodb"
  - "node"
  - "node-js"
  - "react"
  - "react-native"
  - "reactjs"
---

My favorite applications that I've created so far on my own serve a functional purpose. That's why I built [Discog-ify](https://blinkhorn.github.io/discog-ify/select.html) — that application helps people discover new music from record labels they like. I created Memory Palace (MP) this weekend to serve a useful purpose as well.

* * *

Soundtrack: [Blinkhorn](https://soundcloud.com/blinkhorn), “Sketch 6 \| Jupiter”

<iframe width="100%" height="300" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/644931015&amp;color=%23ff5500&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true&amp;visual=true"></iframe>

* * *

MP takes advantage of a memorization technique called the [Method of loci](https://en.wikipedia.org/wiki/Method_of_loci), more commonly referred to as the Memory Palace technique. This clever brain hack takes advantage of the fact that people have a great capacity for quickly remembering spaces, which you can use to help you to easily recall a large amount of sequential information, such as the order of cards that appear in a 52-card deck. For example, it's fairly easy to recall different pieces of furniture in your home and in which order they occur, so if you want to remember the order of the U.S. Presidents, in your mind, you could tie each president to the furniture you see when you walk in your door and around your home. MP allows you to tie pieces of information to images, having the image and information text you want to remember on opposite sides of a virtual card that you can flip.

I first came across the Memory Palace technique in one of [Cal Newport's](https://www.coursera.org/learn/learning-how-to-learn) books, perhaps "[Deep Work.](https://www.amazon.com/Deep-Work-Focused-Success-Distracted/dp/1455586692)" More recently, I came across the Memory Palace technique in the [Learning How to Learn free Coursera Course](https://www.coursera.org/learn/learning-how-to-learn), which I highly recommend. I was originally going to use paper flashcards the Memory Palace technique to memorize some of the more involved AWS processes while studying for the [AWS CDA exam](https://www.coursera.org/learn/learning-how-to-learn), but I don't like having to carry around flashcards, so I built MP instead.

MP is a MERN Stack (MongoDB, Express.js, React, and Node.js) application and you can find the source code on my Github repo [here](https://github.com/blinkhorn/mp). It's not perfect by any means (please excuse the typo on the landing page), but it's a tool that I will use to help me memorize information. Future versions of the application would be built out for mobile, potentially using React Native, and I'd love to eventually use AR to superimpose information I want to memorize on top of the images themselves.

The application is currently not deployed. I hope to refactor and deploy it again in the near future.
