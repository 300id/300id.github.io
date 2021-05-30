---
layout: post
title: "如何搭建类似博主的blog"
description: "The first post"
categories: [教程]
tags: [教程]

---

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
<span id="busuanzi_container_page_pv">
  本文总阅读量<span id="busuanzi_value_page_pv"></span>次
</span>