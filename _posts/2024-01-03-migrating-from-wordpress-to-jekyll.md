---
title: "Migrating from WordPress to Jekyll"
date: "2024-01-03"
categories: 
  - "aws"
  - "blog"
tags: 
  - "aws"
  - "ruby"
  - "jekyll"
  - "wordpress"
  - "javascript"
  - "software-development"
  - "software-engineering"
  - "tech"
---

When I noticed that the hosting plan for the WordPress website where I kept my tech portfolio and blog was about to auto-renew for an embarrassingly high fee, I knew it was time to try something new. So I set off in search of a solution I could implement to easily migrate my WordPress website, including its blog posts, to a cost effective service within AWS that's easy for me to manage and update.

* * *

Soundtrack: Blinkhorn, “Sinergy”
<iframe style="border: 0; width: 400px; height: 120px;" src="https://bandcamp.com/EmbeddedPlayer/album=44496829/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/artwork=small/transparent=true/" seamless><a href="https://blackmagicrecs.bandcamp.com/album/sinergy">Sinergy by Blinkhorn</a></iframe>

* * *


WordPress powers websites the world over, allowing people to write blog posts, including various forms of media if they wish, and have what they create be served on their website for anyone to view. WordPress is a solid solution for non-technically inclined people to share their ideas with the world via their website, which is probably why a significant portion of websites on the internet are still powered by WordPress. As long as non-technical WordPress users using WordPress and any WordPress theme they use to power their website are doing so in a fairly straightforward way, they don't need help from engineers. There are some tradeoffs to consider when using WordPress however.

First off, there are security concerns. When managing a WordPress website, you need to install and configure security plugins in the WordPress management dashboard to protect yourself from brute force along with other types of attacks. Another concern with WordPress in my mind is that the content is stored on a MySQL database, so the typical recommendation if you're moving your WordPress website to another cloud provider is to use a server-based offering there, such as EC2 in AWS. While I recognize that there are still specific use cases for EC2, I prefer to use AWS' serverless offerings to drive down costs, minimize the need for regular maintenance, and make the application scalable if I ever think I'll need that.

Early on in my search to replace my WordPress website with another technology, I knew that I wanted to move to a static frontend website, mainly to remove the need for a database and service layer, which would allow me to dramatically cut costs through a service such as Amazon S3's Static website hosting option. I knew that if I ever needed to write a new blog post or change anything on the website, I could update that in the code myself, and when I did this, it would be great if I could easily configure a pipeline to deploy my changes to the static website when I pushed them up to Github.

I found a few options that I carefully considered, most notably [Hugo](https://gohugo.io/), but I ended up going with the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme for [Jekyll](https://jekyllrb.com/). Once I exported all of my WordPress content, I was able to import it into the Minimal Mistakes theme in Jekyll. From there, I made number of customizations to my website and I minimized the number of images I would be serving on the static website to help decrease the website's load time. Once I had the website looking good in my local development environment, I figured out how to deploy my website to AWS Amplify. Amplify has a new feature since I last used it that allows you to connect your specific repositories within your Github account, and once you do that, CI/CD is ready to go so that whenever I commit and push to the `main` branch in my repository, it's picked up by Amplify and deployed to the hosted website. Last but not least, I ditched the `blinkhorn.tech` domain I was using previously for the much more reasonably priced `blinkhorn.net`, which I reserved on Amazon Route 53 and was able to seamlessly associate with what I deployed via Amplify.

When I was using my `blinkhorn.tech` WordPress site, I had a page on it for the music I make whenever I'm not coding. Aside from my artist bio, the content on `blinkhorn.tech/music` was mostly my music, which I iFramed in from other places. Seeing that everything on my music page could be contained on one page, I marked up a new music page using HTML and CSS (no JavaScript necessary), reserved [blinkhornmusic.net](https://www.blinkhornmusic.net/) on Route 53, and deployed the music page to [blinkhornmusic.net](https://www.blinkhornmusic.net/) via Amplify from a separate repository on my Github.
