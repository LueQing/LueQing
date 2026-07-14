+++
date = '2026-07-14T14:48:03+08:00'
draft = false
title = '数模LaTeX的安装'
tags = ['数模']
categories = ['数模']
+++

## 教程

### TeXLive 安装教程

[https://mirrors.tuna.tsinghua.edu.cn/CTAN/info/install-latex-guide-zh-cn/install-latex-guide-zh-cn.pdf](https://mirrors.tuna.tsinghua.edu.cn/CTAN/info/install-latex-guide-zh-cn/install-latex-guide-zh-cn.pdf)

**[教程-30分钟速通LaTeX】LaTeX排版零基础速成教程，数学建模美赛/科研论文必看视频！！（附赠美赛LaTex模板）](https://www.bilibili.com/video/BV1Mc411S75c)**

国赛模板

[latexstudio/CUMCMThesis: 全国大学生数学建模竞赛LaTeX论文模板 已经适配到 2023 年格式](https://github.com/latexstudio/CUMCMThesis)

[之后找到了更新的模板](https://github.com/Sustainable-Enjoyment/CUMCM-LaTeX-Template)

经过与[**全国大学生数学建模竞赛论文格式规范（2023年修订稿）](https://www.mcm.edu.cn/html_cn/node/b5ab480af29da69a4806e51e714b3de4.html)比对，这个挺符合的\*\*

使用模板时经常有很多编译警告，没啥鸟影响

## 预计耗时

大概只需要一个下午就可以了解普通LaTeX的使用方法(看那个视频)，以后就可以查公式和查模板来写了。

大概要半个下午来了解如何在VSCode使用LaTeX

## 看下来的感受

引用很方便，知网上可以直接导出BibTex里面的文本，对以后科研来说很方便（但是数模一般不引用 刘汉黄豆）

感觉比word规范

熟练使用还需要时间

## 关于数学公式

[在线LaTeX公式编辑器-编辑器](https://www.latexlive.com/)我觉得这个应该也是挺好用的。

# 关于表格

[https://www.latex-tables.com/](https://www.latex-tables.com/)

## 附录的使用

直接看模板的example.tex就可以了解，代码插入的方式也在里面

## 在overleaf中，导入cumcmthesis.cls就可以使用这个数模模板

[https://cn.overleaf.com/9434441518nnfprqbnkjzb#92c7bc这是我跟练后的内容](https://cn.overleaf.com/9434441518nnfprqbnkjzb#92c7bc%E8%BF%99%E6%98%AF%E6%88%91%E8%B7%9F%E7%BB%83%E5%90%8E%E7%9A%84%E5%86%85%E5%AE%B9)

经过检验,overleaf和vscode中的效果一样

## 如果想在VSCode使用LaTeX

[安装TeX live](https://tug.org/texlive/windows.html)

在VSCode中安装**LaTeX Workshop** 插件

配置插件() 在VSCode的settings.json里面

这三种recipes配方，在看完教程视频后就可以知道这有关引用的内容

```jsx
    "latex-workshop.latex.recipes": [
        {
            "name": "xelatex",
            "tools": ["xelatex"],
            // 简单文档，快速编译
        },
        {
            "name": "xe->xe->xe",
            "tools": ["xelatex", "xelatex", "xelatex"],
            // 含有目录、交叉引用，需要多次编译
        },
        {
            "name": "xe->bib->xe->xe",
            "tools": ["xelatex", "bibtex", "xelatex", "xelatex"],
            // 包含参考文献的完整编译链
        }
    ],
    
    // 定义工具链
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",          // 启用反向搜索
                "-interaction=nonstopmode", // 非交互模式，报错不暂停
                "-file-line-error",    // 显示错误行号
                "%DOCFILE%"            // 当前文件名（不含扩展名）
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": ["%DOCFILE%"]
        }
    ],
    
    // 默认选择第一个 recipe（xelatex）
    "latex-workshop.latex.recipe.default": "first",
    
    // --------------------- 辅助功能 ---------------------
    // 保存时自动编译
    "latex-workshop.latex.autoBuild.run": "onSave",
    
    // 编译后自动清理辅助文件（可选）不建议，我开了这个之后引用出错
    //"latex-workshop.latex.clean.fileTypes": [
    //    "*.aux", "*.bbl", "*.blg", "*.idx", "*.ind", 
     //   "*.lof", "*.lot", "*.out", "*.toc", "*.acn", 
    ///    "*.acr", "*.alg", "*.glg", "*.glo", "*.gls", 
    //    "*.ist", "*.fls", "*.log", "*.fdb_latexmk", 
    //    "*.synctex.gz"
    //],
    //"latex-workshop.latex.autoClean.run": "onBuilt",
    
    // 启用反向搜索（PDF 点击跳转到代码）
    "latex-workshop.viewer.pdf.internal.port": 0,
    
    // --------------------- 显示配置 ---------------------
    // 使用 VSCode 内置 PDF 查看器
    "latex-workshop.view.pdf.viewer": "tab",
    
    // 显示编译日志
    "latex-workshop.message.showInfo": false,
    "latex-workshop.message.warning.show": true,
    "latex-workshop.message.error.show": true
```

VSCode还有个LaTeX-utilitiess插件可以方便地导入图片，但是大小宽度还是要自己设置

‍
