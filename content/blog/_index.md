---
title: Blog
---

# Blog
{{% details title="Info about blog" %}}

This section is dedicated to the blog. Here you can find all the articles that I wrote. I will try to write articles that are as clear as possible, keeping a cadence of one article per week. If you have any suggestions or you want to see a specific topic covered, feel free to contact me on [LinkedIn](https://www.linkedin.com/in/federico-melis-5779b218b/).

{{% /details %}}

{{% for post in .Site.RegularPages %}}
{{% if in post.Path "blog" %}}
{{% if eq post.Params.published true %}}
{{% include "blog-card.html" %}}
{{% end %}}
{{% end %}}
{{% end %}}
