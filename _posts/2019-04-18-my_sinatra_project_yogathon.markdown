---
layout: post
title:      "My Sinatra Project: Yogathon!"
date:       2019-04-18 20:16:10 +0000
permalink:  my_sinatra_project_yogathon
---


I really loved working on this project! 

My initial idea was to work create a workouts tracker. Thinking about it a little more though, I decided to make the project aa bit more specific. 

The yoga studio I attend is currently doing a Yogathon. If you complete 25 classes in 30 days. you can be entered to win prizes. As-is, the yogathon is tracked by a physical stickerboard, which, to be honest, works pretty well. But what if I could have a dynamic web application that tracks the yoga classes, and allows people to make comments on each class, and see how others are doing?

I decided to create a yogathon website. I'd have two models: yogaclasses and users. Each user would have_many yoga classes, and each yoga class would belong_to user. 

In addition to the standard CRUD functionality, I also built out a leaderboard so you are able to see how other users are doing, and a profile that gives you a helpful accounting of how many classes you have taken with both specific detials on your class and a running total of how many classes you have left to go.

On Jennifer Pazos's recommendataion, I lauched the app using the Corneal gem, which was tremendously helpful. Corneal is a Sinatra-site generator. With Corneal and a few short commands, I was able to have all of my folders and basic routes set up. It also included some basic styling, which gave my site a more professional look and feel without any additional work on my part. If you ever find yourself starting a Sinatra site from scratch, I'd highly recommend it.

In all, I loved working on this project. I was a bit intimidated out the gate, but I found that the lessons left me well-prepared to make a basic website, which was thrilling. While I certainly encountered errors, I'm finding that I'm becoming more able to intuitively find basic mistakes and quickly correct for them.

...on to the assement, and to Rails!


