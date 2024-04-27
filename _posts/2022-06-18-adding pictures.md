---
title: "Showing images in md.post on GithubPages with Jekyll"
published: true
categories:
  - Blog
  - Coding
tags:
  - Blog
  - GitHub
  - Jekyll
  - minimalmistakes
date: 2022-06-26 00:02 +0100
---
Hi all,
while I was trying to post-add an image in my last post on 'Creating a blog with Jekyll and Github' I encountered differences between my test website on the localhost and on GithubPages.
The image was showing fine on localhost with `![image](/assets/example-image-post.png)` which I also referenced in the front matter block in the upper part of markdown file. Just like in the image below (it's an example post that came with the theme and are the first lines of Peter Pan :smiley:):
<img src="{{site.baseurl | prepend: site.url}}assets/images/example-image-post.png" alt="example-image-post" />

Anyway, this just works for the localhost but not on my GitHub domain. After a long troubleshooting session I found out the problem was that I haven't set up the URL in the `config.yml` file. Stumbled upon this <a href="https://stackoverflow.com/questions/69023928/github-pages-with-jekyll-not-showing-images-in-md-post">solution</a> and it solved my problem.

There are two things to do:
1. URL Set-Up
2. Image Tag Set-Up
<br/>

<br/>
_URL Setup_

In _config.yml just add 2 lines:
```yaml
#_config.yml

url: 'https://your-github-username.github.io/' # your main domain
baseurl: 'your-repo-name/' # if you're using custom domain keep this blank example: baseurl: ''
```

Now we are all set with our URL setup, now edit the link tag in yout markdown file.

_Image Tag Set-up_

```html
<img src="https://your-github-username.github.io/your-repo-name/assets/Untitled.png" alt="Untitled" />
```

Afterwards I still wondered why the image was not shown on Mozilla (my default browser) but on other browsers. Turns out I needed to clear the cache. :laughing:

It's still hard for me to understand the different behaviour between localhost and GithubPages. But I am still a noob...getting there someday.
Thanks for reading and I hope I could help somebody in the internet who encountered the same problem as me.