---
layout: post
title: "如何搭建类似博主的blog"
description: "The first post"
categories: [教程]
tags: [教程]

---
<div id="container"></div>
<link rel="stylesheet" href="https://imsun.github.io/gitment/style/default.css">
<script src="https://imsun.github.io/gitment/dist/gitment.browser.js"></script>
<script>
var gitment = new Gitment({
id: '', // 可选。默认为 location.href
owner: '300id',
repo: '300id.github.io',
oauth: {
    client_id: '33599ca507921d70615d',
    client_secret: '1e6229b3a409aac51d5d51dc5458a9c257ca59a9',
},
})
gitment.render('container')
</script>