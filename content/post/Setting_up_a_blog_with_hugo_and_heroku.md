+++
date = "2015-04-02T14:48:15-04:00"
title = "Setting up a blog with Hugo and Heroku"
description = "My First Post!"
+++

Today I will walk you through how to set up a blog with Hugo and host it on Heroku. It will only take 5 minutes if you already have git installed and a heroku account,

Hugo is a static website engine that takes raw content in various formats (like markdown) and render them into html to be hosted statically.

You can download Hugo [here](https://github.com/spf13/hugo/releases) for your platform. Hugo is a command line tool, so the install is very light. I'm using windows, so I unzipped the windows download, dropped the exe into C:\bin (which I have inclued in my PATH), and renamed the executable to hugo.exe.

Creating your blog
-----

Once you have Hugo installed, You should open your command line (I use powershell) and create your blog:  

  <code class='ps'>hugo new site C:\Blog</code>

Once you switch to the newly created location, you can create your first post!

<code class="ps">cd C:\Blog</code><br/>
<code class="ps">hugo new post/first.md</code>

This creates a markdown file that's your first draft. You should open it up, add some content, and remove the `draft=true` line from the header.

Previewing your blog
---
We're almost ready to preview the blog, but you just need to do one more step before we can see it

<code class='ps'>git clone https://github.com/chrisbye/hyde-x themes/hyde-x</code>

This clones a copy of my slightly customized fork of the hyde-x hugo theme. I'll be making some tweaks to the theme as I use it, so it'll be helpful to get those updates. Otherwise, you can use the original hyde-x theme, or any other hugo theme you'd like. 

Now, you can look at a preview of your blog. Run this next (you can cancel the long-running command with CRTL+C).

<code class='ps'>hugo server \-\-theme=hyde-x \-\-buildDrafts \-\-watch</code>

Open a browser and go to <code>http://localhost:1313/</code> to see your site. Hugo generated your site from the markdown and theme, and it also is watching for changes to your site content so it can update on the fly. 

Try making some changes to your post and saving the changes to watch your preview update on the fly

Right now, nobody can see your site except for you, so let's put this up onto Heroku.
___

Hosting your blog
---

You'll need the [Heroku Toolbelt](https://toolbelt.heroku.com/) installed and an account on heroku before we can put the blog on the web. You'll also need git installed. Go ahead and do that now, I'll wait.

...Good! There are some files that we need to create and modify so that heroku can run our app.

Add the line <code>theme = "hyde-x"</code> to your <code>config.toml</code> file. and create a file called <code>.hugotheme</code> with one line:

<code class=ps>https://github.com/ChrisBye/hyde-x.git</code>

Heroku uses this reference to the theme to get the latest version when you deploy your application. We just need to set up a git repository that we can push up to heroku, so run these lines:

<code class="ps">git init</code><br/>
<code class="ps">git add -A</code><br/>
<code class="ps">git commit -m 'Initial commit'</code>

Now we'll log in to heroku, initialize a heroku app from a new command line session at the root of your blog directory (C:\\Blog) and push our new blog up to the web.


<code class="ps">heroku login</code><br/>
<code class="ps">heroku create \-\-buildpack https://github.com/roperzh/heroku-buildpack-hugo.git</code><br/>
<code class="ps">git push heroku master</code><br/>
<code class="ps">heroku open</code><br/>

If everything went as expected, you should now be looking at your brand-new heroku-hosted blog!

There are many settings and options that can be tweaked to customize every aspect of your blog. when you make changes locally that you want to display, simply commit them to your git repository, and push the changes up to heroku with the commands we used earlier.