---
layout: post
title: "the start of my academic blog"
date: 2020-02-29
---

Okay.

So this marks the beginning of my blog. Mostly I want to use this blog to document my thoughts, or interesting things that I find while undertaking research for my thesis in Electrical Engineering. What am I researching for my thesis? I'm interested in doing something in power systems modelling which uses a Deep Reinforcement Learning agent for control. I think I'll focus on frequency control.

As an aside, I'm pretty stoked with this blog I've built. It's powered by [Jekyll](http://jekyllrb.com) and I can use Markdown to author my posts. It provides support for MathJax so I can create beautiful inline equations such as this cheeky fellow $$ v = i \cdot R $$. Also it provides support for block equations too:

<div style="font-size: 1.5em; color: #333;">$$ e^{i \cdot \pi} + 1 = 0 $$</div>

So how do I make this work? I forget Markdown all the time, because I only use it for README.md files on git. Here you go future Shane: [a Markdown cheatsheet](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf). Also there are couple of commands that you need to remember to serve the content up to your github based webpage. To get your freshly created content built, use the following:
```
bundle exec jekyll build
```
If you want to serve the content to `http://localhost:4000` to have a peek at the joy you are creating, use the following:
```
bundle exec jekyll serve
```

That's it. Don't forget to git commit after creating awesome.