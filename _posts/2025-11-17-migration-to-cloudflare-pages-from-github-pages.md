---
layout: post
title: "Migrating to Cloudflare Pages from Github Pages"
date: 2025-11-17 09:27:00 +0800
categories: general
---

This blog is served using [Jekyll](https://jekyllrb.com/). I initially hosted this blog on Github Pages because of how simple it is to setup a Git repository there with Jekyll workers. However, Github does not provide analytics on site traffic, something in which I was interested.

Migration was pretty simple actually. Cloudflare provides automatic building of Git reposisories from Github and Gitlab. They also provide 500 builds per month, which is more than enough for a personal blog.

The only problem I had was with the build command. Cloudflare uses:

```sh
jekyll build
```
This did not work for me. I had to change it to:

```sh
bundle exec jekyll build
```

Frankly, I do not understand how Ruby builds work, but this fixed the issue for me.

I think Cloudflare Pages would be better for my site in the long run. I wish to add more features to this site. We shall wait and see :)
