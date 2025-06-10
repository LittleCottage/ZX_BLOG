---
title: "Rendering Images in GitHub Pages"
date: 2025-06-10
categories: ["Today I Learned"]
tags: ["Coding", "Hugo", "GitHub", "Frontend"]
---

When I built my [personal blog site](https://littlecottage.github.io/ZX_BLOG/) with [Hugo Texify3](https://themes.gohugo.io/themes/hugo-texify3/) and tried deploying it [using GitHub Pages](https://gohugo.io/host-and-deploy/host-on-github-pages/), something very weird happened: for [a blog](https://littlecottage.github.io/ZX_BLOG/posts/2025-01-26-ce-evaluation/) containing images, while those images can be shown locally under the URL `http://localhost:1313`, they cannot be rendered under GitHub Pages. 

After muddling this issue with GitHub Copilot embedded in VS Code for hours, eventually ChatGPT saved my day. The reason is actually simple: in the post, the image was initially referenced as 

```
![case 1 visualization](/images/2025/case_1.png)
```

This works fine locally (it resolves to `./static/images/2025/case_1.png`) but breaks remotely (it resolves to `https://littlecottage.github.io/public/images/2025/case_1/png` while the correct location is `https://littlecottage.github.io/ZX_BLOG/public/images/2025/case_1/png`).  So a quick fix is updating the reference to 

```
![case 1 visualization](/ZX_BLOG/images/2025/case_1.png)
```

so that it resolves to the correct path both locally and remotely. To ensure that the path was searched in an absolute way rather than relatively, then adding the statement

```
canonifyURLs = true
```

to the `hugo.toml` configuration file so that Hugo converts all relative URLs to absolute URLs using `baseURL = https://littlecottage.github.io/ZX_BLOG/`. 

The learned lesson is:

1. When an object failed to display in the browser, 99% is a path specification issue.

2. Trust ChatGPT more than Copilot. 

A complete chat history with ChatGPT [is here](https://chatgpt.com/share/68488b35-6a9c-8012-8bf3-0013a4bc95f2). 