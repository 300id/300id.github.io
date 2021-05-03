---
layout: post
title: "如何搭建类似博主的blog"
description: "The first post"
categories: [教程]
tags: [教程]

---
<!-- Gitalk 评论 start  -->

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
		id: '2021-05-02-how-to-build-a-blog', 注意id一定不要重复，这里是举个例子，可以写中文，如果重复了，就会把其他地方的评论显示过来
    
    });
    gitalk.render('gitalk-container');
</script> 
<!-- Gitalk end -->
