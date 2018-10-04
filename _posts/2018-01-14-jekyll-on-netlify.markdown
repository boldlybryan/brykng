---
title: Deploying a Jekyll Site on Netlify
date: 2018-01-14 19:00:00 Z
layout: post
thumbnail: "/images/posts/blog-with-jekyll-and-netlify.jpg"
preview: Explaining how I created this blog and how it's deployed.
---

About a month ago, I launched a redesigned version of this very website. Previously, I'd just had a one page site and then an instance of Ghost running on a subdomain. At first, I tried moving the whole thing to Ghost, but abandoned that idea when I realized that the platform wasn't built for my needs. After that, I tried out GatsbyJS after jumping into React. It's a really great static site generator, but I couldn't help from thinking how I was just reinventing the wheel. That wheel was Jekyll.

I ran my site with Jekyll for a couple of years in 2015 and 2016. I don't really remember why I left. As best as I can remember, I just felt like the blogging workflow was a bit cumbersome. I was inexperienced at the time and never able to figure out a good deployment solution. So, I resorted to running builds locally and then uploading changes via FTP to my server. But this is no longer the case, as I've figured out this insanely good set-up for running my website.

What you'll need:
* Local installation of [Jekyll](https://jekyllrb.com)
* Comportable using a command line interface
* A [GitHub](https://github.com), GitLab, or Bitbucket account (Can also use self-hosted git repository)
* [A free Netlify account](https://netlify.com)

First things first, you're going to need a local instance of Jekyll. It's built on Ruby, so you're going to need that installed too before we can create a website. If you don't have it, I suggest googling `Install Ruby on {insert operating system here}`. Seriously, there are so many ways to install and manage Ruby, with different nuances depending on your OS. I'm using Bash on Windows inside Windows 10 and use rvm for installing Ruby. When in doubt, you can always hop onto the command line and type `ruby -v` to check if you have it, and if you do what version you have. As of January 2018, Jekyll needs Ruby 2.2.5 or above. Also, check to make sure you have GCC and Make installed, per the Jekyll docs.

With that out of the way, we can now install Jekyll. In your CLI, navigate to the directory where you keep your web projects. From there, type `gem install jekyll bundler`. All of the dependencies will be installed along with Jekyll itself. It may take a few minutes, but once thats done, we're ready to create our new site.

Back in your CLI, type `jekyll new blog`, where "blog" is whatever name you'd like for your new site. Once the site is built, type `cd blog` to navigate into the directory for your blog. Then, type `bundle exec jekyll serve` and you'll see a message in the terminal that a local server is running on port 4000. That's it! Well, sort of. This is the default set-up for Jekyll, meaning you'll have the out-of-the box theme called Minima, along with some other template files that are used to create your website. Feel free to peruse the Jekyll documentation to figure it all out. Install a new theme and edit the content of your site. Come back when you're ready to deploy!

At this point, you have the first round of updates made on your site. Maybe you even have some new content in the form of blog posts and updated page content. Hopefully, you've also been using GitHub (or similar) to keep track of your changes to the site. If you haven't already, sign up for a GitHub account. Make sure you push all of your changes to your Jekyll site out to GitHub.

Once all your code is in GitHub, head over to app.netlify.com and login or create an account. After that, click on the "New site from Git" button. You'll be prompted to select a Git provider where your site's source code is stored. Click on GitHub, and you'll be asked to sign in and grant access to Netlify. Do what it says, then select the repository for your site when your list of repos is displayed.

Then, you'll be asked to configure the build settings for your site. In my experience, everything was already filled out for a Jekyll deployment. If not already filled in, make sure that you have the master branch selected as the branch to deploy. Your build command will be `jekyll build` and the publish directory is `_site`. Once you verify that your build settings are correct, click on the deploy button. Your Jekyll site is now hosted on Netlify.

Now, any time that there are changes on your site's master branch Netlify will pull down the newest code, run your Jekyll build, and deploy the changes to your server. If you keep an eye on the Netlify dashboard, it will tell you whether it is published, building, or if the build failed. You can even set up integrations with other services or add email notifications if certain events occur in Netlify.

By default, your site will be stored on a randomly named subdomain of netlify.com. While this could be great if you're trying stuff out, your personal website should be on a domain that you own. Luckily, Netlfiy supports this, too! In the Netlify control panel, click on the Domain settings button. You'll get sent into the domain management tab in the site settings. Under custom domains, you can click add a domainand enter your domain name to the site. After that, they'll provide some instructions for pointing your domains nameservers to Netlify.

I was surprised to see my changes propogate in the matter of minutes. Once everything was wired up, I set up my security certificates and forced all traffic through HTTPS. I had to wait about an hour to configure this, but it was a breeze to get working.

Did I mention that everything mentioned above is **FREE**?!? Jekyll is of course open-sourced, while GitHub and Netlify offer free accounts. And I'm not even taking full advantage of all Netlify has to offer. Here are just a few feautures I'll be taking advantage of as I continue to enhance my site:

* Branch preview deployments
* Build snapshots and the ability to roll-back to previous version
* A/B split testing
* HTML form submissions

I'm super excited about this set-up. Jekyll provides me a simple way to create new content. It's very easy to create new templates or make enhancements to existing ones. And to have changes deployed instantly is quite a treat!

If you have an troubles with any of this, try to troubleshoot using the documentation provided by Jekyll and Netlify (both are excellent, BTW). For some more environment specific things, Google will prove useful. Of course, if you have any questions about any of this, please [tweet at me](https://twitter.com/brykng). I'll do what I can, and if I'm unable to help I'll try to point you in the right direction. If you end up trying this out, feel free to let me know, too!