0. 使用命令更新资源库
   `git submodule update --remote`
1. 登录 github 以及设置登录验证
2. 修改/book/hugo.toml里面的

```
theme= 'hugo-book'
languageCode = 'zh'
defaultContentLanguage = 'zh'
hasCJKLanguage = true
```

3. 修改 theme 里的 i18n为

```
- id: bookSearchConfig
  translation: |
    {
      encode: false,
      tokenize: function(str) {
        return str.replace(/([\x00-\x7F] | ' ')/g, '').split('');
      }
    }
```

目录结构
自我介绍
我的简历

引言.(介绍一下这个项目的背景，以及这个项目的的基本目录结构，类似pmq, 这个项目更多的会是面向技术人员，里面也可以涉及到我的个人简历)

1. 基本概念

   1. 介绍这个项目能做什么呢
   2. 一些项目的基本概念（中文已经完成，缺少图片）
2. 快速开始

   1. 如何启动起来一个简单实例(中文完成，缺少图片)
3. 功能特性（可以支持哪些功能，中文已经完成）
4. 客户端（客户端的使用，以及一些基本的部署，中文完成，缺少图片）
5. 运维部署
6. 权限控制和登录
7. 界面操作（中文完成，缺少图片）
8. 用户常见 QA(等待写)
9. 个人简历
