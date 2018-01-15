---
layout: post
title:  "Deploying a Jekyll Site on Netlify"
date: 2018-01-14 12:30:10 -0500
cover: /images/posts/blog-with-jekyll-and-netlify.jpg
thumbnail:
preview: Explaining how I created this blog and how it's deployed.
---
About a month ago, I launched a redesigned version of this very website. Previously, I'd just had a one page site and then an instance of Ghost running on a subdomain. At first, I tried moving the whole thing to Ghost, but abandoned that idea when I realized that the platform wasn't built for my needs. After that, I tried out GatsbyJS after jumping into React. It's a really great static site generator, but I couldn't help from thinking how I was just reinventing the wheel. That wheel was Jekyll.

I ran my site with Jekyll for a couple of years in 2015 and 2016. I don't really remember why I left. As best as I can remember, I just felt like the blogging workflow was a bit cumbersome. I was inexperienced at the time and never able to figure out a good deployment solution. So, I resorted to running builds locally and then uploading changes via FTP to my server. But this is no longer the case, as I've figured out this insanely good set-up for running my website.

What you'll need:
* Local installation of Jekyll
* Comportable using a command line interface
* A GitHub, GitLab, or Bitbucket account (Can also use self-hosted git repository)
* A free Netlify account

First things first, you're going to need a local instance of Jekyll. It's built on Ruby, so you're going to need that installed too before we can create a website. If you don't have it, I suggest googling `Install Ruby on {insert operating system here}`. Seriously, there are so many ways to install and manage Ruby, with different nuances depending on your OS. I'm using Bash on Windows inside Windows 10 and use rvm for installing Ruby. When in doubt, you can always hop onto the command line and type `ruby -v` to check if you have it, and if you do what version you have. As of January 2018, Jekyll needs Ruby 2.2.5 or above. Also, check to make sure you have GCC and Make installed, per the Jekyll docs.

With that out of the way, we can now install Jekyll. In your CLI, navigate to the directory where you keep your web projects. From there, type `gem install jekyll`. All of the dependencies will be installed along with Jekyll itself. It may take a few minutes, but once thats done, we're ready to create our new site.

Back in your CLI, type `jekyll new blog`, where "blog" is whatever name you'd like for your new site. Once the site is built, type `cd blog` to navigate into the directory for your blog. Then, type `jekyll serve` and you'll see a message in the terminal that a local server is running on port 4000. That's it! Well, sort of. This is the default set-up for Jekyll, meaning you'll have the out-of-the box theme called Minima, along with some other template files that are used to create your website. Feel free to peruse the Jekyll documentation to figure it all out. Install a new theme and edit the content of your site. Come back when you're ready to deploy!

At this point, you have the first round of updates made on your site. Maybe you even have some new content in the form of blog posts and updated page content. Hopefully, you've also been using GitHub (or similar) to keep track of your changes to the site. If you haven't already, sign up for a GitHub account. Make sure you push all of your changes to your Jekyll site out to GitHub.

Once all your code is in GitHub, head over to app.netlify.com and login or create an account. After that, click on the "New site from Git" button. You'll be prompted to select a Git provider where your site's source code is stored. Click on GitHub, and you'll be asked to sign in and grant access to Netlify. Do what it says, then select the repository for your site when your list of repos is displayed.

Then, you'll be asked to configure the build settings for your site. In my experience, everything was already filled out for a Jekyll deployment.

If you encounter errors...

Setting up a domain, https

Talk about other perks of Netlify: CDN, branch preview deployments, build snapshots, split testing, HTML form backend, amd more.