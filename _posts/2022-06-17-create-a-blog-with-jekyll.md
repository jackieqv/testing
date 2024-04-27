---
title: "Creating a blog with Jekyll and Github"
published: true
categories:
  - Blog
  - Coding
tags:
  - Blog
  - GitHub
  - Jekyll
  - minimalmistakes
date: 2022-06-23 00:02 +0100
---
Hi all, my first post will be about my experience of how I set up this blog with Jekyll and Github. 
First things first, there are many ways to create a blog. You can use website builders like Jimdo or Wix, where you build your website in minutes using online drag and drop tools. Another very popular choice is WordPress, an online content management system (CMS), which is more complex but you basically use an editor on the graphical user interface to build it and you can add pre-built plug-ins to extend functions on your website. No programming skills needed. 
If you are looking for a easy way to implement your own blog without learning how to code, these options above are for you.

For myself, I wanted to gain technical skills and learn coding, so I took the <a href="https://www.coursera.org/learn/html-css-javascript-for-web-developers">HTML, CSS, and Javascript for Web Developers</a> course on coursera.org, already having in mind to build my own website afterwards (also I really recommend the course! It was a great mix of theory and hands-on assignments). After completing the course, I was still quite overwhelmed to build up a website from scratch, so I began researching and stumbled upon Jekyll, a static site generator written in Ruby. I found the blogging theme of <a href="https://mmistakes.github.io/minimal-mistakes/">minimal mistakes</a>, which I really liked and wanted to use as a template for my blog. The ready-made theme can be cloned from GitHub to your repository and local computer and makes it easier to start right away. Another strong argument for me to build my blog with Jekyll was that it works well with GitHub Pages and allows me to deploy my site for free. 

It was quite a challenge for me to work with the command line for the installation and set up. It was a lot of trial and error for the installation and configuration but when it worked it's like magic is happening :satisfied:

Prerequisites to get started to build your website with Jekyll and Github:
- Install Visual Studio Code (or a similar code editor)
- Create an account on Github.com for hosting your website on <a href="https://pages.github.com">GitHub Pages</a>

Here are the high-level steps I took to build my website with Jekyll:
1. Decide for a Jekyll theme: This <a href="https://github.com/topics/jekyll-theme">link</a> provides different themes to choose from.
2. Clone the theme from the Github repository: I used the remote theme starter of <a href="https://github.com/mmistakes/mm-github-pages-starter">Minimal Mistakes</a> and cloned it as a preconfigured theme to my own repository.
3. Clone your online repository to your local folder.
4. Install Ruby: Use the documentation on <a href="https://jekyllrb.com/docs/step-by-step/01-setup/">Step by Step Tutorial</a> to set up the installation.
5. Configuration: Open your local folder with the cloned repository in Visual Studio Code and replace the sample content with your own and configure as necessary. Test your configuration on the local host.
6. Deployment: I used GitHub to host my site which is freely hosted on GitHub's `github.io` domain; Push to GitHub and publish on GitHub Pages. You can also host it under your custom domain or you can use other host providers.

For me, it's a wonderful first project to get into coding and there's still so much to unpack and learn. I learned the most through trial and error and searching for solutions in developer forums. It has been challenging but also fun.
Here are the sources that helped me most:
- <a href="https://talk.jekyllrb.com/">Jekyll Forum</a>
- <a href="https://stackoverflow.com/questions/tagged/jekyll">Stack Overflow Forum</a>

Also check out this awesome blog on how to build a static website with Jekyll and Github Pages (it's amazingly explained!): <a href="https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages#command-line-tools-suite-">Programming Historian</a>

Here is where my editing happens (in Visual Studio code with Markdown files): 
<img src="{{site.baseurl | prepend: site.url}}assets/images/screenshot-editing.png" alt="screenshot-editing" />


I will post about certain challenges I've encountered in the future and I might add other features and improvements into this blog as well over time.


Stay tuned :heartbeat:

