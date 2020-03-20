---
layout: post
title: Adopting Jekyll
---

So I finally installed Jekyll in my local, forked a <a href="https://github.com/barryclark/jekyll-now" target="=blank">starting point</a> from GitHub, customized it and committed. It literally took me less than 30 minutes to get it up and running (I already had my blog subdomain pointing to my GitHub page, and CNAME modified there). I also had to install 3 missing gems locally, but that's no biggy. The mere fact that it was so straightforward to install and get it running, convinced me that I should look no further.

I am very much conscious that it's a static generator and I won't expect it to do any dynamic voodoo in the future. It suits my minimal needs for my blog. I am currently using Atom editor with a core markdown viewer. It's simple, light, clean, and I'm happy with it. Jekyll has much more to offer, besides the features that I'm currently using, and I'll definitely look into those.

Below is a quick walkthrough of how to install Jekyll, fork a starting point, and test the site locally.

1. Install Jekyll

    ```
    $ gem install jekyll
    ```

2. Run the local server

    ```
    $ jekyll serve
    ```

    If you encounter some dependency error similar to :

    ```
    jekyll 3.1.1 | Error:  jekyll-feed
    ```

    , just install it manually as such :

    ```
    $ gem install jekyll-feed
    ```

3. Open the site in your browser

    ```
    http://localhost:4000
    ```

    or

    ```
    http://127.0.0.1:4000
    ```

You should now be able to see the homepage of the site, slick and clean. Below is how the website's directory structure should look like.

```
├─ CNAME # Contains your custom domain name (optional)
├─ _config.yml # Jekyll's configuration flags
├─ _includes # Snippets of code that can be used throughout your templates
│  ├─ analytics.html
│  └─ disqus.html
├─ _layouts
│  ├─ default.html # The main template. Includes <head>, <navigation>, <footer>, etc
│  ├─ page.html # Static page layout
│  └─ post.html # Blog post layout
├─ _posts # All posts go in this directory!
│  └─ 2014-3-3-Hello-World.md
├─ _site # After Jekyll builds the website, it puts the static HTML output here. This is what's served!
│  ├─ CNAME
│  ├─ LICENSE
│  ├─ about.html
│  ├─ feed.xml
│  ├─ index.html
│  ├─ sitemap.xml
│  └─ style.css
├─ about.md # A static "About" page that I created.
├─ feed.xml # Powers the RSS feed
├─ images # All of my images are stored here.
│  ├── first-post.jpg
├─ index.html # Home page layout
├─ scss # The Sass style sheets for my website
│  ├─ _highlights.scss
│  ├─ _reset.scss
│  ├─ _variables.scss
│  └─ style.scss
└── sitemap.xml # Site map for the website
```

After building the site, two additional folders are created :

```
├─ _site # Contains all static generated code after build
├─ .sass-cache # Contains templates cached by Sass
```

Those two folders won't be versioned as GitHub pages will generate pages from the sources and those should be included in .gitignore.

If you want to go deeper into customization and hosting on your GitHub account, you might find <a href="https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/" target="_blank">this post</a> very handy.
