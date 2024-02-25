---
title: "Black Magic Recordings' Companion Web Application"
date: "2023-07-25"
categories: 
  - "aws"
  - "blog"
  - "js"
  - "music"
  - "vue"
tags: 
  - "aws"
  - "javascript"
  - "software-development"
  - "software-engineering"
  - "tech"
---

When I want or need to learn a new technology, my favorite way to gain those skills is to come up with an idea for an application that interests me and then leverage the technology I'm learning to build out that idea. Last summer, I needed to learn Vue.js, so during a vacation to the Chesapeake Bay, I had a lot of fun building out a companion application for a record label that didn't exist yet, all while sitting on a dock on the Chesapeake Bay.

* * *

Soundtrack: Blinkhorn x Carrier Signal, “Divide”

<iframe style="border: 0; width: 400px; height: 120px;" src="https://bandcamp.com/EmbeddedPlayer/album=1478268035/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/artwork=small/transparent=true/" seamless><a href="https://blackmagicrecs.bandcamp.com/album/divide">Divide by Blinkhorn x Carrier Signal</a></iframe>

* * *


After a few coding sessions on that dock, I had a working full stack serverless companion application that leveraged AWS Lambda (Python and Node.js), API Gateway, Amazon S3, DynamoDB, Amazon Cognito, and a Vue.js UI, all tied together by AWS Amplify.

The application looked sleek to my eyes, so I bought a domain name for it on Route 53, which remains the only part of the application I have had to pay anything for on AWS (the rest has stayed in the free tier, +/- $0.02 a month).

In the Black Magic Recordings (BMR) companion web application, users can enter a code that they receive in a PDF when they buy and download a release from BMR's Bandcamp page. When they enter the code, they are directed to a page on the UI that prompts them to create and validate an account with their email address; if they already have an account, they can sign in using their credentials. Once authenticated, users can follow the the prompts in the BMR companion application to download the previous BMR release for free as a 320 kbps MP3, which is shared with the user via an S3 Presigned URL that expires after 6 minutes. After 6 minutes have elapsed and the Presigned URL expires, the MP3 file that the user downloaded is programmatically removed from the S3 bucket. You can find much of the code for the BMR companion web application [here](https://github.com/blinkhorn/black-magic) on my Github.

Besides the core business logic for the BMR companion web application, I created [a separate Python Lambda function](https://github.com/blinkhorn/black-magic-distribute-mp3s) that distributes the MP3 files I upload to BMR users so that the files are available to the users when they buy a BMR release and redeem the code they receive in their download from Bandcamp.

When coding the BMR web application, I built aspects of the Vue 3 UI and the Python API in tandem. My Python API uses [Powertools for AWS Lambda (Python)](https://docs.powertools.aws.dev/lambda/python/latest/) so that I could expose multiple API endpoints on the same Lambda function, which better enables the sharing of functionality across the API endpoints and streamlines the API deployment process. Once I had the Vue.js application spun up on localhost, I made use of [AWS SAM](https://aws.amazon.com/serverless/sam/) so that I could build a Docker image of the Python API, run the API locally, and send requests to the API from the localhost UI, which invoked the Lambda code and helped me confirm the functionality I engineered.

Given that I had a well-designed, scalable, low-cost application, I decided to explore the record label idea further. I came up with a business plan and reached out to a good friend of mine who is also musically inclined to see if he was interested in pairing with me on the idea. The friend, Alex Rubenstein, was interested in working on the idea with me, but we needed an impressive logo, so I reached out to my friend and former colleague Fady Rizk, told him the idea for our record label, and conveyed to him what we were thinking of for the logo design. Fady was willing to help, and while he was iterating on the logo design, Alex and I reached out to multiple people we know who run record labels and they gave us invaluable advice. When Fady delivered the logo, Alex and I made a more formal announcement and solicited demos from musicians whose music we wanted to highlight. We formally started Black Magic Recordings in May 2023 when we had a runway of releases lined up and signed. After kicking off the record label with [a "pay what you want" single called "Divide"](https://blackmagicrecs.bandcamp.com/album/divide) that is a collaboration I worked on with [Carrier Signal](https://carriersignal.bandcamp.com/), the BMR catalog formally started with BMR001, [a single from our friend Chris Kennedy](https://blackmagicrecs.bandcamp.com/album/hey-whats-up).

BMR primarily releases singles that go live on Bandcamp the third Thursday of each month and are released on all other digital platforms the next day. The catch phrase for BMR is "sounds for six days" because the singles are available for $2 the first six days and then the release price jumps, which we've already found encourages listeners to buy the release early, before the price goes up. When enough fans buy the release in the initial six days after the release goes live on Bandcamp, the release garners more attention on Bandcamp and can lead to the music having a snowball effect of fans buying the music en masse. The business model — encouraging fans to buy good quality music early and including an extra MP3 with each Bandcamp download via the BMR companion web application to sweeten the deal — helps support the artists whose music BMR releases via the label's generous profit split with the artists in addition to sustaining BMR longterm.

The BMR companion web application isn't publicly advertised by design; instead, the web application is intended to be an Easter egg of sorts that people who buy the music on BMR's Bandcamp will receive a link to with the code they can enter to get a bonus MP3. If you'd like to try out the web application, buy [our latest release on Bandcamp](https://blackmagicrecs.bandcamp.com/album/system-boot). Ri Caragol - "System Boot" \[BMR002\] is available for $2 until tomorrow (7/26/23):

<iframe style="border: 0; width: 100%; height: 120px;" src="https://bandcamp.com/EmbeddedPlayer/album=3143852685/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/artwork=small/transparent=true/" seamless><a href="https://blackmagicrecs.bandcamp.com/album/system-boot">System Boot by Ri Caragol</a></iframe>
