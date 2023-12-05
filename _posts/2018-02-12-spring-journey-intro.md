---
title: "My Spring Journey: Introduction"
author: true
date: "2018-02-12"
categories: 
  - "blog"
  - "java"
  - "spring"
tags: 
  - "ambient-music"
  - "code"
  - "coder"
  - "computers"
  - "intelij"
  - "intelij-idea"
  - "java"
  - "java-spring"
  - "java-spring-boot"
  - "programmer"
  - "programming"
  - "software-development"
  - "software-engineering"
  - "spring"
  - "spring-boot"
  - "tech"
---

I started getting back into Java this year. A mentor recommended that I work with the Java Spring framework. To familiarize myself with Spring, I did what I normally do when I want to learn a new code related — I looked for an example of a simple functioning Spring application on Github. The first project I found seems to be the essential introductory application to Spring — [Spring Petclinic](http://projects.spring.io/spring-petclinic/). Apparently Spring Petclinic dates back to the beginning of the Spring framework. I take it that there are many more possibilities for Spring than are demonstrated in Spring Petclinic, but I read that the Spring community still has a soft spot for Spring Petclinic.

* * *

Soundtrack: [Rewak](https://soundcloud.com/rewakmusic) vs. [Blinkhorn](https://soundcloud.com/blinkhorn), "Wallaby"

<iframe src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/320833007&amp;color=%23ff0000&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true&amp;visual=true" width="100%" height="200" frameborder="no" scrolling="no"><span data-mce-type="bookmark" style="display: inline-block; width: 0px; overflow: hidden; line-height: 0;" class="mce_SELRES_start">﻿</span><span data-mce-type="bookmark" style="display: inline-block; width: 0px; overflow: hidden; line-height: 0;" class="mce_SELRES_start">﻿</span></iframe>

* * *

After launching and playing around with the application locally, I opened Spring Petclinic in InteliJ IDEA to get a better sense of the project structure. At its core, Spring Petclinic seems to be broken into five packages: model, owner, system, vet, and visit. Within model, there are BaseEntity.java, NamedEntity.java, and Person.java classes. The other four packages also have Java classes in them, and there seems to be a good logic to the inheritance in the project.

Spring Petclinic gave me a good glimpse into what a Java Spring application looks like under the hood, and I've started modeling my first Java Spring application, [Beat Browser](https://github.com/blinkhorn/beat-browser), off of it. Stay tuned for more posts on My Spring journey and please excuse my Java Spring naiveté along the way.
