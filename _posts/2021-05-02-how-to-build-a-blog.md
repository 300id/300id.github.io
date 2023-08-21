---
layout: post
title: "这是一篇用来测试的空白文章"
description: "The first post"
categories: [教程]
tags: [教程]

---

> This is [kramdown][kramdown] formatting test page for [Simple Texture][Simple Texture] theme.

* Kramdown table of contents
{:toc .toc}

# General Usage

This is a normal paragraph.

This is [a link](https://yizeng.me) to my homepage.
A [link](https://yizeng.me/blog "Yi Zeng's Blog") can also have a title.

This is a ***text with light and strong emphasis***.

This **is _emphasized_ as well**.

This *does _not_ work*.

This **does __not__ work either**.

This is a footnote[^1].

This scarcely known tag emulates <kbd>keyboard text</kbd>, which is usually styled like the `<code>` tag.

This tag should denote <ins>inserted</ins> text.

The emphasize tag should _italicize_ text.

This tag will let you <strike>strikeout text</strike>.

## Blockquotes

> ruby -v
>
> tsc -v

### Nested

> This is a paragraph in blockquote.
>
> > A nested blockquote.
>

### Lists inside

> Unordered List
> * lists one
> * lists two
> * lists three
>
> Ordered List
> 1. lists one
> 2. lists two
> 3. lists three

### Long lines

> Jekyll is a simple, blog-aware, static site generator perfect for personal, project, or organization sites. Think of it like a file-based CMS, without all the complexity. Jekyll takes your content, renders Markdown and Liquid templates, and spits out a complete, static website ready to be served by Apache, Nginx or another web server. Jekyll is the engine behind GitHub Pages, which you can use to host sites right from your GitHub repositories.

## Lists

* list 1 item 1
  * nested list item 1
  * nested list item 2
  * nested list item 3 with blockquote
> ruby -v
>
> tsc -v
* list 1 item 2
* list 1 item 3

## Tables


* Table 1

    |-----------------+------------+-----------------+----------------|
    | Default aligned |Left aligned| Center aligned  | Right aligned  |
    |-----------------|:-----------|:---------------:|---------------:|
    | First body part |Second cell | Third cell      | fourth cell    |
    | Second line     |foo         | **strong**      | baz            |
    | Third line      |quux        | baz             | bar            |
    | Footer row      |            |                 |                |
    |-----------------+------------+-----------------+----------------|

* Table 2

    |---
    | Default aligned | Left aligned | Center aligned | Right aligned
    |-|:-|:-:|-:
    | First body part | Second cell | Third cell | fourth cell
    | Second line |foo | **strong** | baz
    | Third line |quux | baz | bar
    | Footer row

## Horizontal Rules

* * *

---

  _  _  _  _

---------------

## Images

Here comes an image!

<a class="post-image" href="https://kramdown.gettalong.org/overview.png">
<img itemprop="image" data-src="https://kramdown.gettalong.org/overview.png" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

## Code highlight


<details> 
    <summary>展开代码</summary>
    {% highlight cpp %}
    #include <bits/stdc++.h>
    #define endl '\n'
    #define ll long long
    #define PB push_back
    #define POP pop_back
    #define INF 0x3f3f3f3f
    using namespace std;
    const int maxn = 1e5 + 10;
    int n;
    string s;
    map<string, int> m;
    int main(){			

    cin >> n;
        int x = 0, ans = 0;
        while(n --){
            cin >> s;
            m[s] += 1;
            if(m[s] == x + 1){
                ans ++;
                x ++;
            }
        }
        cout << ans;
        system("pause");
        return 0;
    }
    {% endhighlight %}
</details>


[^1]: This is a footnote.

[kramdown]: https://kramdown.gettalong.org/
[Simple Texture]: https://github.com/yizeng/jekyll-theme-simple-texture

<!-- Link Gitalk 的支持文件  -->
<link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
<script src="https://unpkg.com/gitalk@latest/dist/gitalk.min.js"></script>
<div id="gitalk-container"></div>
<script type="text/javascript">
    var gitalk = new Gitalk({

    // gitalk的主要参数
        clientID: '33599ca507921d70615d',
        clientSecret: '1e6229b3a409aac51d5d51dc5458a9c257ca59a9',
        repo: '300id.github.io',
        owner: '300id',
        admin: ['300id'],
        id:'2021-05-02-how-to-build-a-blog',

    });
    gitalk.render('gitalk-container');
</script>
<!-- Gitalk end -->

<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
<span id="busuanzi_container_site_uv"><br>
  本站总访客数<span id="busuanzi_value_site_uv"></span>人次
</span>
