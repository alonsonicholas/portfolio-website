---
title: My Website!
date: 2026-02-24
author: Nicholas Alonso
image: web900x400.png
image_caption: Hello there! :)
---
## Welcome to my website!

Hello, as you have probably gathered from the title of this post, this is my new website. I have had a website for a couple of years now but I hadn't really done anything with it and I ended up abandoning it. Part of the reason I abandoned my initial website was because I wasn't very happy using Wordpress to manage my site. Don't get me wrong, Wordpress is an amazing tool, but I felt it too restrictive and clunky to use for what I wanted and I wanted a better solution to manage everything. So I decided to just make my own from the ground up!

## Background

So I've never actually created a website in HTML and CSS before, at least not with tons of help from the various amounts of LLMs out on the internet now. I gained experience with HTML and CSS  through design sprints for my UX design classes in which I (with a group of people) created UX design prototypes in HTML and CSS. The bulk of these projects were vibe-coded but I did tweak a lot of things manually since the AIs would sometime have trouble understanding what exactly I wanted done. 

These small bits of manual intervention led to me realizing that, it isn't really that hard to do this by hand. I am also in the process of fixing up many broken components of my family's business that is built through WordPress. There are many things that I wanted that the Elementor editor wasn't capable of handling directly, so I would just code these parts in manually. So when it came time to redesign my website, and I looked through hundreds of prebuilt themes that were offering WAY too much for what I wanted, I knew then that coding it by hand was the way to go. In this post I'll go over how I designed my website, the challenges I went through while designing it, and future things to come!

## Step 1. Planning

For my website, I decided to do what I admittedly have failed to do on many projects before and that is planning my site out (goes to show I learn from my mistakes!). I already had a rough idea in my head of what I wanted so I decided to make a diagram of my website in Freeform, and choose the colors and have a general idea of the layout I wanted. 

![First draft mockup of my website](/draft1sitedesign.jpeg)

While planning, my goal was simple, develop something that looks nice, is easy to navigate, and just works. Sure there are very impressive sites out there that have done amazing things, but I have always had an appreciation for simple designs that don't overcomplicate things. I am also not a web developer by any means so something simple was the way to go.  In the image above you can see my initial layout with my website, and while it is not exactly what I ended up going with, it served as an excellent mockup of how I wanted the overall layout of my website to go. I ended up not implementing the Contact page since I thought it was too much complication to add in a separate system to contact me, when I have all my socials displayed front and center. I was also concerned that I would receive spam through a contact form, much like I did on the previous version of my website. On the left and right sides you can see some text that references in animations I wanted to implement on my website, which I still plan on doing but I have zero experience with JavaScript so I decided I'd leave it for later.

While I was designing my layout in Freeform, I realized that I had no way to easily make posts when I wanted to. I wasn't familiar with the concept of Content Management Systems (CMS) so when it came time to think of a way to make blog posts, I settled on just making a new HTML file everytime I wanted to make a post. Then I opened up VSCode and got to work and that's when I quickly realized why that is a HORRIBLE idea. So I did what anyone else does in this day and age, and I conferred with Claude on the best solution. 

Claude brought up Hugo, a Static Site Generator (SSG) that isn't actually a CMS but it was capable of doing exactly what I wanted. I had come across Hugo when looking at other websites, but I was under the impression that it was similar to WordPress, in that it had its own themes that worked with it and those were the only themes I could use. This obviously went against what I wanted but after Claude's assurances that it would simply "just work" with my design I decided that was enough research and I trusted it. Now I should've done more research on my own like I normally do, but I was eager to get started so I just went for it. This wasn't a big mistake, but it definitely added to a lot of the issues I'll touch on later on. 

## Step 2. Designing

This was actually the most straightforward, but time consuming, part of this entire project, believe it or not. The entire development process lasted around 16 hours, with the bulk of my code being from scratch. I created my homepage, and a style guide page. The style guide page was intended for me to style as many things I could think of within CSS, so that when I was ready to make a blog post, I already knew how my site would look, seen below.

![Image of the style guide mockup I made to test out CSS styling of everything I'd use in my blog posts](/styleguide.jpg)

Now I did have Claude help me out with responsiveness on my site, as I really struggled to adapt my website to most devices. Claude was able to easily take care of the responsiveness issues and after a weekend of work I was done with the design. In my CSS file I commented around the sections that Claude took care of for transparency reasons. I (hopefully) structured my HTML in a way that screen readers can be used easily and I used the WAVE tool by WebAIM to make sure all the colors had appropriate contrast to satisfy WCAG AAA requirements since I knew that these were things people struggled with.

I've always liked the idea of making software accessible to everyone no matter what it is, so I brought that mentality into my website. I have yet to make tests to verify everything works as intended, but accessibility will always be at the forefront of my mind for everything I add into my site. Even if only one person benefits from it it was worth the implementation! 

## Step 3. Implementation

Alright, this is the part where I ran into all sorts of trouble. After I had my 2 HTML files and CSS file, I decided now was the time to implement Hugo. Like Claude said, it's just install it put in a couple lines of code and we're ready to go live, right? When I went back to Claude and I asked how exactly the process was done, it informed that it was wrong and if I wanted to use my own website's design I actually had to massively overhaul my website and that it may be more trouble than it's worth. At this point I was on the second day of developing my website with almost no breaks in between and it was around 11PM, so I just wanted to make my site public and be done with it and my dreams were seemingly crushed! I spent the next 2 hours reading Hugo's documentation and not understanding anything being said, asking various LLMs to walk me through the process of converting my site to be used by Hugo only for them to get it massively wrong. The information overload and brain fog fully kicked in at this point and I decided to take the defeat, and leave it for the next day. 

The next day, I sat down with a clear head and carefully read through Hugo's documentation only to realize that it truly was simple. See, Hugo follows a strict file structure, and my main challenge was understanding this file structure due to Claude being wildly incorrect. After reading the documentation, I realized it's actually pretty straight forward and I followed Hugo's file structure as explained in its documentation. Hugo then uses template variables to identify things such as titles, author names, and really whatever else you want. These defined fields are referred to as "Front matter".  Once you put these template variables into the appropriate section of your HTML file, Hugo handles it from there. Newly created markdown files your front matter and you simply fill out the fields and everything after that in your markdown file is content. 

Then just run 

```
hugo
```

In your terminal and Hugo will create a "public" folder. Simply upload all these folders to your "public_html" folder in your hosting provider's file manager and you have a working site! In my case, I uploaded my files to a Github repo and used the "Git version control" feature in cPanel to handle the uploading of the files, but you could really upload them however is best for you. After this, I realized that I don't have a way to create the cards on my homepage for my projects, so I did a bit more digging and found out that this could be handled in a very similar fashion to the blog posts, with the exception that I'd have to use a YAML file instead of markdown, but this was very straightforward. Now as soon as I want to upload a post, I can write out the post in markdown, create the card in my YAML file that links to my post, and just upload those files to my hosting provider! (Note: the process is a bit more tedious than this but I'm already working on a way to speed this up!)

Now I don't want to downplay the work that went into this, so I want to note that I learned all this after about another 5-6 hours of researching and almost giving up on Hugo altogether. Total development time was about 22 - 23 hours but for my first time actually programming a website, I think the amount of time I spent was fair and the end result is something I am extremely proud of!

## So what's next?

This site is by no means finished, there is still so much I want to implement like proper animations that scroll you down between sections instead of the abrupt snap that happens when clicking on the header buttons, an index for longer posts so that readers can quickly read the section they're most interested in, a page with all my posts and the ability to filter through them through tags and content, and other things that I'll probably think of later on down the line. 

Like many projects, this website will probably never be truly done and will go through many changes so I'll document the changes I make as I go along and as I go through my IT/Cyber journey, this site will evolve to fit my needs. 

For now though, I just hope that you enjoyed reading through this and take some inspiration from it to go out and just build what you want, even if you're unsure of how the end result will look!

