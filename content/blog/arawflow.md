---
title: "How to post a blog here (META)"
date: 2020-08-30T14:53:26+08:00
draft: true
tags: ["hugo", "blog"]
---

Dear Isya,

Last year, we came to an agreement to make a blog that would reflect some of our musings that we can share to the public.
Araw Seekers the blog has existed since.

## Static Site choice

While our first choice was to create [one](https://arawseekers.wordpress.com/) using WordPress, I realized later on that that platform is bloated.
So many widgets, plugins, and other applications that we will never use.
These unnecessary stuff affect loading times of a site. 
Since our use case is only a small blog, we ditched the dynamic content management system of big names like WordPress or Blogger, and opted for something called static site generator.

As the name implies, it generates a static site, which you could think of as a "traditional" websitewhere all content consists of HTML files.
This is good for our use case, because it means faster loading times due to it requiring less processing power.
Not only that, but bloated websites contribute to huge power consumptions in data centers and servers around the world. 
Since le Internet is big, one can imagine the implications on our environment. 
All the more we should "slim down" our site. 

I picked [Hugo](https://gohugo.io) at the time of this site's creation, for no particular reason other than it's supposed to be one of, if not *the*, fastest static site generators out there.

## The Workflow

Now, I will try to explain the work flow when creating and/or editing a blog entry to be posted here.
Since we will be mainly working on your MacBook Pro, any commands will only consider that environment.

### Prelims
First, open the following programs:
- Terminal (where you will type commands later)
- Atom, or any text editor (where you will edit the blog entries)
- Firefox, or any web browser (where you will view the rendered site)

> **TIP**: Make use of the Spotlight by pressing `⌘ + Space`, and start typing the name of the programs above.

### Step 1: Go to our site's folder

In the terminal, enter `arawseekers`.
This is an *alias* (a shortcut for a command, usually shorter than the original) that will bring you to `isyaferrer/Sites/arawseekers/` folder. 

### Step 2: Create New Post

If you will edit an existing post, skip this step and proceed to the Step 3.

If you are starting a new entry, enter in the terminal: `hugo new content/posts/xyz.md`.
Let's break down that command:
- `hugo new` generates a new, blank post
- `content/posts` is the relative folder in which this new file is placed. You can replace this with other folder path, but that's out of the scope (quite literally) of this entry.
- `xyz` is the would-be title of the blog post. Although you can edit this later, make it relevant to the post. Mind also the `.md` (markdown) file extension as this is important.

### Step 3: Content Creation

Using the Atom editor, open the file.

The top part is called the front matter.
This is the post's metadata that usually includes the title post, date and time of creation, tags, etc., all of which can be edited.

You can start the blog entry after the front matter.

	---
	title: "How to post a blog here (META)"
	date: 2020-08-30T14:53:26+08:00
	draft: false
	tags: ["hugo", "blog"]
	---
	Dear Isya,
	
	Last year, we came to an agreement to make a blog that would reflect some of our musings that we can share to the public.
	Araw Seekers the blog has existed since.


Now that's meta.

Since you will be editing this in a markdown file, I suggest you [familiarize yourself with markdown](https://www.markdownguide.org/cheat-sheet).

#### The small matter of compressing images

As mentioned earlier, static sites load faster. 
Usually. 
We can maintain this trait by not uploading high quality images.

To compress any image you might include in a post, upload them first in [TinyJPG](https://tinyjpg.com).
You can upload "up to 20 images, max 5 MB each". 
After compressing all the images, download them all and paste them in `isyaferrer/Sites/arawseekers/static/images/`.
You can now refer to the images in this folder path.

>**TIP**: If you're using the [hardened Firefox](https://www.privacytools.io/browsers/#addons), then you can bypass the 20-image limit of TinyJPG.
Just quit the browser, reopen, and revisit TinyJPG.
This should clear the cookies stored in the browser.
Rinse and repeat as needed.

### Step 4: Checking the Content

Now that you have content, you may want to know how it looks as a blog post.

In the terminal, enter `hugo server`.
This command renders the site for preview in the browser.
As long as this is running in the terminal, changes made (and saved) in Atom are immediately reflected in the browser, which can be viewed when you enter `localhost:1313` in the URL bar.

Also, you can't input new commands while this is running in the terminal.
You may want to open a new instance of terminal if you're going to input some new command.

Press `control + C` to stop the rendering, thus freeing the terminal.

Here's a sample terminal output:

	                   | EN   
	-------------------+------
  	Pages            |  47  
  	Paginator pages  |   0  
  	Non-page files   |   0  
  	Static files     | 165  
  	Processed images |   0  
  	Aliases          |   6  
  	Sitemaps         |   1  
  	Cleaned          |   0  
	
	Built in 744 ms
	Watching for changes in /Users/isyaferrer/Sites/arawseekers/{archetypes,assets,content,data,layouts,static,themes}
	Watching for config changes in /Users/isyaferrer/Sites/arawseekers/config.toml
	Environment: "development"
	Serving pages from memory
	Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
	Web Server is available at //localhost:1313/ (bind address 127.0.0.1)
	Press Ctrl+C to stop

And here's how it would look like in the browser:

{{< figure src="/images/meta.png" alt="screenshot of the blog" position="center" style="border-radius: 8px; max-width:100%;hei    ght:auto;" caption="Now that's meta." captionPosition="center" captionStyle="color: 297298;" >}}

### Step 5: Finalizing the Content

If you're satisfied with how everything is laid out, you're almost done.

If you haven't yet, press `control + C` in the terminal to stop the site rendering and to free up the terminal.

Still at the terminal, enter `hugo`.
This command will create the HTML files and put them all in the `isyaferrer/Sites/arawseekers/docs/` folder.

### Step 6: Going Live

In the terminal, enter `arawpush`. 
It's another alias that invokes a simple shell script that "pushes" our HTML files from the previous step to the GitHub server, where our blog is currently hosted for free.

The shell script, aptly named **arawpush.sh**, is a file containing a series of commands that accomplish several tasks.

For transparency, here are the commands written in **arawpush.sh**:

	#!/bin/sh

	git add .
	git commit -m "some surprise adds and/or edit/s"
	git push -u origin master


If that doesn't make sense, it's okay. Just enter `arawpush` in the terminal and it will execute the last three lines of the script without the need to type them all out. *Ayos!*

## Congrats!

You have shared a new blog post to our two readers!
May we share more together!

## Parting thoughts

More than a year after creating this blog, I am realizing that Hugo, too, is a massive tool whose documentation can be confusing, especially for those who aren't too keen on reading them on their free time.
I *might* consider using a [simpler static site generator](https://www.romanzolotarev.com/ssg.html), but this also means overhauling the site, which neither of us has the time nor the patience to do... yet.
For now, Hugo will do.

Anyway, I hope you found this informative.
If not, you know where to find me. ;)

xoxo0xox0ox00xxooXX++xx+0+0x+0x,  
Ohio

`-(o-`
