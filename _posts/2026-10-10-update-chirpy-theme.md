---
title: Update Chirpy Theme
date: 2026-10-10 14:21:00 +60
image: https://i.postimg.cc/T3zwWGng/chirpy-img.png
categories: [Tutorials, Programing]
tags: [websit, github]
summary: How to update chirpy theme for jekyll
---

## Introduction

---
After a while the theme gets outdated compared to the current being developed chirpy theme. 
We need to update it to look like the current version from the developers.

## Procedure

Go to the [Chirpy Starter repo](https://github.com/cotes2020/chirpy-starter/) on Github

Check and compare the contents of the Gemfile

Copy all code inside [Gemfile](https://github.com/cotes2020/chirpy-starter/blob/main/Gemfile)

Replace the code inside local Gemfile in your Visual Code Studio with the new code copied from Github

Run `bundle update` to the update Chirpy

```bash
bundle update jekyll-theme-chirpy
```

---

## Conclusions

Also if you deploy to github pages, if there's a change in the [pages deployment workflow file](https://github.com/pcdrills/blog/blob/main/.github/workflows/pages-deploy.yml) you'll also need to update yours on your repo to look the same.

---

Bye for now. 

---

Follow | [Facebook Page](https://facebook.com/pcdrillsofficial/) | [Telegram Channel](https://t.me/pcdrills/) | [Twitter Handle](https://twitter.com/pc_drills) | [Youtube Channel](https://youtube.com/pcdrills)

