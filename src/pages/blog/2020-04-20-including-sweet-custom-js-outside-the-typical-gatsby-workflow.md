---
templateKey: blog-post
title: Including sweet custom JS outside the typical Gatsby workflow
date: 2020-04-20T21:47:54.065Z
description: >-
  So you have some sweet custom JS script you want to include in your Gatsby
  site? You can’t get the Gatsby plugin to work? There isn’t a plugin for it.
  Oh, the pain.
featuredpost: true
featuredimage: /img/blog-index.jpg
tags:
  - plugins
  - implementation
---
So you have some sweet custom JS script you want to include in your Gatsby site? You can’t get the Gatsby plugin to work? There isn’t a plugin for it. Oh, the pain.



Gatsby has you covered. You can definitely insert custom JS into your Gatsby site, but…



### Should you?[Yes, yes I should](https://docs.google.com/document/d/1KJkXGdIdsPRILdcxhjq9nCM0fhGZmZlyL0-EooQruN0/edit#heading=h.q9wvpzu53ige)

You should try to find a plugin from the[Plugin Library](https://www.gatsbyjs.org/plugins/)first. You’ve probably heard of the programming mantra, Don’t Repeat Yourself. Let’s extend it to Don’t Repeat Others.



There are a whole lot of Gatsby Plugins and it is now pretty rare to find a problem that hasn’t already been solved by others. It takes time to solve problems and you can probably get 80% of the way there with a 20% solution.



Gatsby Plugins also tie into the Gatsby architecture by using its APIs so you will be missing out if you create your own solution.



Have you really looked for a plugin? When you are searching for a plugin for Gatsby make sure you check the[Plugin Library](https://www.gatsbyjs.org/plugins/)fully. Sometimes there’s a less popular plugin lurking further down in your search results that fits your purpose perfectly. Also, Google.



### What about a package?

Ok, I guess there isn’t really a plugin for your problem. The next thing to check would be an NPM package. Yup, just standard JavaScript and React patterns.



Plugins are prepackaged integrations with core Gatsby APIs and what you’re doing may not even require a plugin. Most of what we do is just JavaScript or React, and Gatsby packages it up and puts a nice bow on it.



Stick with the Don’t Repeat Others mantra and try some of the available NPM packages for your problem.



### Roll your own

You could make either a plugin or a package. This is how our community grows, and you could show off your awesome dev skills. Not to mention, you could enlist the help of other developers should you get stuck.



### There’s an app for that

I mean a plugin. With this plugin, you can load your sweet JS script if it’s placed in your static folder at the root of your project. It is also useful for loading scripts that are hosted externally (actually that’s what it was built for).



[Gatsby-plugin-load-script](https://www.gatsbyjs.org/packages/gatsby-plugin-load-script/)



This method carries the benefit of loading your script after the body. Your performance will thank you.



Question for you, “Have you thought about maintaining this project 6 months from now? How about 6 years?”



When you come back to your project and look for how this script was loaded, one of the first places you’ll check is your package.json. And boom, it’ll be right there.



I think this is your best option for adding in your beautiful, awesome JS script to your Gatsby site. But there are other ways as well.

### Wear your Helmet

You could try including your sweet, awesome JS script in the Helmet. This keeps things in the typical Gatsby build pathway. Plus you can place the script tag where it makes the most sense for you, and Helmet will place it in the head tag of your bundled HTML.



<https://stackoverflow.com/questions/54834930/how-to-include-local-javascript-on-a-gatsby-page/54844686#54844686>



One pitfall of placing your scripts in the Helmet is they can slow down the performance of your site. If you don’t want to take that hit, then...

### Cover your ass

You can append custom JS at the end of your compiled body with gatsby-ssr.js. This is how that[plugin](https://docs.google.com/document/d/1KJkXGdIdsPRILdcxhjq9nCM0fhGZmZlyL0-EooQruN0/edit#heading=h.opau9ru8iqje)works. To be honest, I don’t know why you would write this yourself, but you may have your reasons...



<https://github.com/gatsbyjs/gatsby/issues/11013#issuecomment-610886184>