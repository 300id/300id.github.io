---
layout: post
title: "latex配置于vscode教程"
description: "没啥说的"
categories: [教程]
tags: [latex, vscode]

---

> This is [kramdown][kramdown] formatting test page for [Simple Texture][Simple Texture] theme.

* Kramdown table of contents
{:toc .toc}

# TeX Live 下载与安装
[下载地址](https://tug.org/texlive/acquire-iso.html)

1. 进入 ISO 下载页面，点击图示红框圈画位置进入随机的镜像网站。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/1.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/1.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

2. 点击红框圈链接进行 TeX Live 下载。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/2.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/2.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

3. 如果下载速度过慢，可以返回前一页面，进行重新点击，随机进入另一镜像网站进行下载尝试，直到下载速度在您的可接受范围内即可。或者在前一页面，点击 "mirror list" 进入镜像列表，然后手动选择某一镜像网站进行下载。

4. 找到下载好的压缩包，右键，在打开方式中选择“Windows 资源管理器"打开。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/3.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/3.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

5. 找到 "install-tl-windows" 文件，为了后面不必要的麻烦，右键以管理员身份运行。会先出现下图，无需理会，等会儿会消失。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/4.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/4.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

6. 出现下图后，需要进行路径的更改；由于 TeX Live 自带的 TeXworks 不怎么好用，并且此文主要将 vscode 作为 LaTeX 的编辑器，故而取消 安装 TeXworks 前端的选项，再点击安装。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/5.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/5.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

7. 当出现下图所示弹窗时，说明安装完毕，点击关闭即可。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/6.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/6.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

8. 检查安装是否正常： 按 win + R 打开运行，输入cmd，打开命令行窗口；然后输入命令xelatex -v ，如下图
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/7.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/7.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>
如上图所示，若输出了一些版本信息，则安装正常。

# LaTeX的支持插件 LaTeX Workshop安装及配置

1. 点击拓展图标，打开拓展；输入"latex workshop"，选择第一个LaTeX Workshop插件；点击"install"进行安装，等待安装完成；

2. 如图点击设置图标, 点击设置, 打开设置json文件。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/8.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/8.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

3. 按照如下配置json文件
如果你本来这里面就有内容，就直接把下面括号里的复制到最后就行。
<details> 
    <summary>展开json配置代码</summary>
    {% highlight json %}
    {  

    //------------------------------LaTeX 配置----------------------------------
        // 设置是否自动编译
        "latex-workshop.latex.autoBuild.run":"never",
        //右键菜单
        "latex-workshop.showContextMenu":true,
        //从使用的包中自动补全命令和环境
        "latex-workshop.intellisense.package.enabled": true,
        //编译出错时设置是否弹出气泡设置
        "latex-workshop.message.error.show": false,
        "latex-workshop.message.warning.show": false,
        // 编译工具和命令
        "latex-workshop.latex.tools": [
            {
                "name": "xelatex",
                "command": "xelatex",
                "args": [
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "%DOCFILE%"
                ]
            },
            {
                "name": "pdflatex",
                "command": "pdflatex",
                "args": [
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "%DOCFILE%"
                ]
            },
            {
                "name": "latexmk",
                "command": "latexmk",
                "args": [
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "-pdf",
                    "-outdir=%OUTDIR%",
                    "%DOCFILE%"
                ]
            },
            {
                "name": "bibtex",
                "command": "bibtex",
                "args": [
                    "%DOCFILE%"
                ]
            }
        ],
        // 用于配置编译链
        "latex-workshop.latex.recipes": [
            {
                "name": "XeLaTeX",
                "tools": [
                    "xelatex"
                ]
            },
            {
                "name": "PDFLaTeX",
                "tools": [
                    "pdflatex"
                ]
            },
            {
                "name": "BibTeX",
                "tools": [
                    "bibtex"
                ]
            },
            {
                "name": "LaTeXmk",
                "tools": [
                    "latexmk"
                ]
            },
            {
                "name": "xelatex -> bibtex -> xelatex*2",
                "tools": [
                    "xelatex",
                    "bibtex",
                    "xelatex",
                    "xelatex"
                ]
            },
            {
                "name": "pdflatex -> bibtex -> pdflatex*2",
                "tools": [
                    "pdflatex",
                    "bibtex",
                    "pdflatex",
                    "pdflatex"
                ]
            }
        ],
        //文件清理。此属性必须是字符串数组
        "latex-workshop.latex.clean.fileTypes": [
            "*.aux",
            "*.bbl",
            "*.blg",
            "*.idx",
            "*.ind",
            "*.lof",
            "*.lot",
            "*.out",
            "*.toc",
            "*.acn",
            "*.acr",
            "*.alg",
            "*.glg",
            "*.glo",
            "*.gls",
            "*.ist",
            "*.fls",
            "*.log",
            "*.fdb_latexmk"
        ],
        //设置为onFaild 在构建失败后清除辅助文件
        "latex-workshop.latex.autoClean.run": "onFailed",
        // 使用上次的recipe编译组合
        "latex-workshop.latex.recipe.default": "lastUsed",
        // 用于反向同步的内部查看器的键绑定。ctrl/cmd +点击(默认)或双击
        "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click",



        //使用 SumatraPDF 预览编译好的PDF文件
        // 设置VScode内部查看生成的pdf文件
        "latex-workshop.view.pdf.viewer": "external",
        // PDF查看器用于在\ref上的[View on PDF]链接
        "latex-workshop.view.pdf.ref.viewer":"external",
        // 使用外部查看器时要执行的命令。此功能不受官方支持。
        "latex-workshop.view.pdf.external.viewer.command": "D:/300id/SumatraPDF/SumatraPDF.exe", // 注意修改路径
        // 使用外部查看器时，latex-workshop.view.pdf.external.view .command的参数。此功能不受官方支持。%PDF%是用于生成PDF文件的绝对路径的占位符。
        "latex-workshop.view.pdf.external.viewer.args": [
            "%PDF%"
        ],
        // 将synctex转发到外部查看器时要执行的命令。此功能不受官方支持。
        "latex-workshop.view.pdf.external.synctex.command": "D:/300id/SumatraPDF/SumatraPDF.exe", // 注意修改路径
        // latex-workshop.view.pdf.external.synctex的参数。当同步到外部查看器时。%LINE%是行号，%PDF%是生成PDF文件的绝对路径的占位符，%TEX%是触发syncTeX的扩展名为.tex的LaTeX文件路径。
        "latex-workshop.view.pdf.external.synctex.args": [
            "-forward-search",
            "%TEX%",
            "%LINE%",
            "-reuse-instance",
            "-inverse-search",
            "\"D:/300id/Microsoft VS Code/Code.exe\" \"D:/300id/Microsoft VS Code/resources/app/out/cli.js\" --ms-enable-electron-run-as-node -r -g \"%f:%l\"",
            "%PDF%"
        ],
        "markdown-preview-enhanced.previewTheme": "github-dark.css"
    }
    {% endhighlight %}
</details>

**注意其中有个别处需要改成你自己的路径** 

前面两个红线画出的位置填写下一步安装的PDF所在的路径，后面两个记得改成你vscode所在的安装路径。

<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/9.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/9.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

# SumatraPDF下载、安装、配置

1. 其安装很简单，与通用软件安装过程一致，记得更改安装路径并记住，下文配置需要使用其路径。
[官网下载链接](https://www.sumatrapdfreader.org/download-free-pdf-viewer)
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/10.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/10.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>


2. 记得在这里改成你的安装路径。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/9.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/9.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

3. 打开SumatraPDF，点击左上角设置，之后点选项
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/11.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/11.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

4. 然后在红框处输入以下代码, 注意路径改成你的vscode对应的安装路径。
<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/12.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/12.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

```shell
"D:/300id/Microsoft VS Code/Code.exe" "D:/300id/Microsoft VS Code/resources/app/out/cli.js" --ms-enable-electron-run-as-node -r -g "%f:%l"
```


# 快捷键设置以及最终效果展示

1. 为了更方便进行编译，可对其设置快捷键，设置快捷键步骤如下。然后在json文件里添加如下内容。

<a class="post-image" href="{{site.url}}/images/2023-10-12-latex-on-vscode/14.jpg">
<img itemprop="image" data-src="{{site.url}}/images/2023-10-12-latex-on-vscode/14.jpg" src="/assets/javascripts/unveil/loader.gif" alt="Kramdown Overview" />
</a>

<details> 
    <summary>快捷键配置代码</summary>
    {% highlight json %}
    [
        {
            "key": "alt+q", // 编译
            "command": "latex-workshop.recipes"
        },
        {
            "key": "alt+s", // 搜索
            "command": "latex-workshop.synctex",
            "when": "editorTextFocus && !isMac"
        },
    ]
    {% endhighlight %}
</details>


2. 然后随便找个tex的仓库clone下来。
[github 链接](https://github.com/300id/Latex-Chinese-ACL.git)


3. 使用编译快捷键然后选择编译方式
**xelatex -> bibtex -> xelatex*2**
然后选中你的tex代码，使用搜索快捷键，就会自动打开PDF软件，并自动跳转到代码所对应PDF里的内容。同样的，双击PDF的文字，
也会自动跳转到对应代码处内容。


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
        id:'2023-10-12-latex-on-vscode',

    });
    gitalk.render('gitalk-container');
</script>
<!-- Gitalk end -->

<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
<span id="busuanzi_container_site_uv"><br>
  本站总访客数<span id="busuanzi_value_site_uv"></span>人次
</span>
