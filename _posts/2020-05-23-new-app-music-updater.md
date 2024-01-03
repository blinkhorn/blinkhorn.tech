---
title: "New App: Music Updater"
date: "2020-05-23"
categories: 
  - "aws"
  - "js"
  - "music"
  - "react"
---

Today [my company](https://fiscalnote.com/) gave us a "Get Ahead Day." I used this opportunity to hone my MongoDB, Express, React, and Node.js (MERN stack) skills by creating a fun new application. The application is called Music Updater (MU) and it allows users to get the latest releases from record labels and artists they want to stay up-to-date on. 

* * *

Soundtrack: Smoke & Tea - Sunday Afternoon
<iframe style="border: 0; width: 560px; height: 435px;" src="https://bandcamp.com/VideoEmbed?track=123626746&bgcol=ffffff&linkcol=0687f5" mozallowfullscreen="1" webkitallowfullscreen="1" allowfullscreen="1" seamless></iframe>

* * *
    

The application retrieves artist and record label releases from [Discogs](https://www.discogs.com/)' API and lets users store their favorite releases.

Future features that could be added to this application include cron jobs that automatically check artist/record label releases and notify the user via email when one of their artists/record labels has a new release. It would also be cool to use Spotify's API to generate playlists for the user with music they gathered from their favorite artists / record labels.

Besides these added features, I acknowledge that the design / UX of this MVP (minimum viable product) version of MU could be improved on. For one thing, I would like to have a loading spinner to indicate that the app is working on fetching releases from an artist / record label with an extensive discography (that takes some time).

If you have any suggestions, please send me a message [here](https://blinkhorn.net/contact/). And if you want to make additions or edits to the code, please submit an issue in the [Github repo](https://github.com/blinkhorn/music-updater) and we can take it from there!

The project is currently not deployed, but I may redeploy it in the next few months. Thanks for reading — have a good weekend!
