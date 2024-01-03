---
title: "New Full-Stack Serverless App: Most Supported Record Labels"
date: "2022-01-09"
categories: 
  - "angular"
  - "aws"
  - "blog"
  - "js"
---

To give some context for this personal learning project I recently started, over the last year, I've learned a lot about AWS and coding Python Lambda functions in addition honing my production-grade Angular skills. Last month, I even became AWS Solutions Architect - Associate certified. So over winter break, I started thinking about building a full-stack serverless application for a fun learning project.

* * *

Soundtrack: Blinkhorn - Sligo

<iframe style="border: 0; width: 400px; height: 439px;" src="https://bandcamp.com/EmbeddedPlayer/album=3886873479/size=large/bgcol=ffffff/linkcol=0687f5/artwork=small/transparent=true/" seamless><a href="https://notyetremembered.bandcamp.com/album/sligo">Sligo by Blinkhorn</a></iframe>

* * *

To minimize costs and maximize scalability, I ensured that the AWS infrastructure for this project was entirely serverless. I used DynamoDB as the data store and a Python AWS Lambda function that made use of the of the [Lambda Powertools Python open source library by AWS](https://awslabs.github.io/aws-lambda-powertools-python/latest/) that has a number of neat features including the ability to turn a lambda function into a multi-endpoint REST API backed by AWS Gateway. On the front-end, I used Angular 13 in an [Nx monorepo](https://nx.dev/) and AWS Cognito for Sign Up and Sign In features. Since using Nx at work, I've become sold on it, especially for production-grade Angular applications since it ships with Jest, Cypress, it's very easy to create a [NestJS](https://nestjs.com/) mock API for your Angular app in the same repo for local development and testing. Besides that, the Nx Console extension for VS Code allows you to easily generate new Angular libraries, components, services, etc. If you want to learn more about Nx with Angular, I highly recommend [this course from Lukas Ruebbelke on Frontend Masters](https://frontendmasters.com/courses/production-angular/). The front-end for this application, and for that matter, the backend too, are very simple — I wanted to use this project as a chance to try out what I've learned about serverless infrastructure in AWS for something simple and fun.

The application lets you search for record labels and pull data for them from [Discogs' API](https://www.discogs.com/). Specifically, I have business logic that pulls the 50 most recent releases from the record label you search for and then searches for how many people "own" and "want" each release. At that point, I developed a simple algorithm that scores the record label based on the average release data.

I started the project by building several REST API routes using AWS SAM, which has a feature that lets you test your Lambda function locally using Docker. Once I confirmed that I was able to pull data down from Discogs and come up with a score that could then be stored in DynamoDB, I deployed the Lambda using AWS SAM and confirmed the ability to store data in DynamoDB.

After developing the backend, I moved onto building a simple UI. I have seen a lot of people writing about [Amplify](https://aws.amazon.com/amplify/) lately, so I decided to give it a try. The Amplify docs for Angular along with [this blog post](https://dev.to/beavearony/getting-started-with-a-angularnx-workspace-backed-by-an-aws-amplify-graphql-api---part-1-24m0) on configuring Amplify for Angular in an Nx monorepo were particularly useful. The Amplify CLI has a number of commands you can run to add authentication, storage, and an api to the Amplify project, which I used. Due to this, I ended up moving a lot of the Python Lambda API logic into the UI repo and tweaking it there, so most of the code is in my [UI repo](https://github.com/blinkhorn/most-wanted-labels-ui).

The project is not currently deployed. Whenever I deploy it again, I intend to make it mobile responsive and fix a number of bugs.

Some tricky parts of development included CORS as is often the case in front-end development, but not for any of the typical reasons! Lambda Powertools Python's documentation has an outdated import code snippet for their CORSConfig usage example, so I had to go into their source code for an example of the correct usage. Besides that, Discogs' API documentation was outdated, so I had to guess what some of the correct endpoints were until I found what I needed.

There are also some items that I wish worked better. Amplify definitely makes deployment easier and I wish there were more examples in their documentation that catered towards production-grade Angular applications using Nx (good thing I found the blog post I listed above!). For instance, I wish the Amplify request functions leveraged Observables instead of Promises since Observables are fairly standard in Angular. It's also really cool that you can create an API and link it to your UI using the Amplify CLI, and in the future, I hope there will be documentation on how to easily link an Amplify UI you deploy to a REST API you deploy using AWS SAM.

I hope you enjoyed this post. If you have any questions, comments, or decide to give something similar a try, I'd love to hear about it where I share this blog post (I've disabled comments on here).
