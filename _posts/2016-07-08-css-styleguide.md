---
layout:     post
title:      CSS Styleguide
summary:    Creating a styling framework
published: true
categories: code
---

In looking to improve my working knowledge of Angular 1.x I recently completed an excellent tutorial on thinkster.io. Following this I wanted to make something to put some of the things learnt into practice, however whilst planning the project I questioned how I was going to style the front-end. Sass was my obvious language of choice having experience with it from before, but I wondered if I was going to use a styling framework or not. 

Whilst at GA, we always used a styling framework, be it Bootstrap, Semantic UI, Foundation or similar as we were producing projects in a very short space of time and if you want ready made UI components with a strong sense of design then these are great, however when working with designers on a project these become a bit restrictive.

The go-to man for CSS is Harry the Wizard (CSS Wizardry). He writes some excellent articles on his website and has given some very interesting talks, perhaps most notably in this case his talk on ITCSS (Inverted Triangle CSS) which describes a structure for writing modular, scalable css. This led me to InuitCSS, a modular style framework by CSS Wizardy that 'helps you do your job faster but doesn't do it for you'. It provides a structure for styling your site but doesn't come packaged with any design or javascript. You can also install as many or as few of the modules as you require, removing the annoyance of having to download a whole styling framework even if only using a few elements from it. So this seemed pretty good, a useful and robust framework that allows for easy customisation.

Whilst exploring InuitCSS and experimenting with it I built a nav bar using flex box. I then came to explore the layout grid module and noted it was using 'inline-block' to display. I couldn't help but question why I would be using flex box and inline-block together, surely flex box should be able to handle all of this on it's own.

Bulma.io is a css framework wholly based on flex box. I really like it but of course it once again comes with design baked in. I needed something that was modular and without design like InuitCSS but based around flex box. I therefore decided to write my own framework based on an ITCSS structure, taking in elements of InuitCSS but but based heavily on the operability of Bulma - without the design baked in.

As I was looking to practice setting up an Angular 1.x project a UI for the framework seemed a good idea and the results can be seen at <https://github.com/benlayer291/css-library>.