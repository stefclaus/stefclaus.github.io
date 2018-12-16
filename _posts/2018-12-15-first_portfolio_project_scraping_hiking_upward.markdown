---
layout: post
title:      "First Portfolio Project: Scraping Hiking Upward "
date:       2018-12-15 23:25:57 -0500
permalink:  first_portfolio_project_scraping_hiking_upward
---



I started my first portfolio project  three weeks ago. And I think I (basically) finished today!

I felt really nervous about starting this project. I felt anxious about coding without the safety net of the tests. As it turns out, it was totally fun and I was totally ready to do it.

Here are a few things I wish I could have known at the beginning.

**Take the time to learn how to use binding.pry. **

I skated through the Ruby lessons without a through and deep understanding of how to effectively use binding.pry. Until this point, I mostly used the tests to guide me to what was wrong with my code. 

I pretty quickly figured it out over the course of this project. I feel really good about using it now, but I wished I had used it more intensively before: that would have saved me some time. (I think there is also a study group on this topic.)

**You're going to need at least a little bit of command line. **

I learned my command line from Learning Python The Hard Way (so thanks, Zed) but it's not taught here formally (I think? Possible I missed it.) You're not going to know a ton, but you should at least know: 

cd: change directory (move from one place to another)
pwd: print working directory (ie, where am I?)
ls: list directory (ie, what's here?)
../ : move up a level in the folder hierarchy
./ : move down a level in the folder hierarchy

**Check to make sure your chosen website doesn't use javascript. But you can use Capybara/Poltergeist if it does.**

You can't scrape a website that uses javascript with Nokogiri. Check your chosen site carefully to make sure that it doesn't use javascript. 

I didn't follow this advice, and had written out a lot of my project by the time I realized that the reason the scraper on my index page didn't work was because my index page (https://www.hikingupward.com/maps/) used javascript!

Probably-too-obvious-but-it-wasn't-to-me-pro-tip: If anything on your page is responsive, it's using javascript.

I ended up scraping the site with Capybara/Poltergeist, which worked fine! So not the end of the world if your site does use javascript, but you'll need to learn an additional skill that isn't taught in the program.

**Study The Sample Projects Closely.**

Really understanding how the World's Best Restaurants gem, the Student Scraper gem, and the Daily Deals gem work is hugely helpful. Spend some time with these before you get started.

**You can totally do this! But carve out some quiet time**

I'm a part-time student and I have a full-time job. Prior to this project, I was finding good success working a few hours here and there, sometimes in the front of the TV, sometimes while also doing other small tasks at home. 

I found that in order to make good forward progress on this project, I had to carve out significant chunks of time. It just took me awhile to get in the right frame of mind and hammer forward on a problem. So I committed to a marathon day of coding on Sundays working out of the beautiful WeWork Dupont, and gave myself a bit more of a concerted break on Saturdays. This really helped me get through the project.

Good luck! 
