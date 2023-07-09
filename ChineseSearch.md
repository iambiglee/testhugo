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

1. 基本概念
   1. 介绍这个项目能做什么呢
   2. 一些项目的基本概念
   3. 我为什么要做这个项目
2. 快速开始
   1. 如何启动起来一个简单实例
3. 领域模型
4. 功能特性
5. 客户端
6. 运维部署
7. 权限控制和登录
8. 界面操作
9. 用户常见 QA
10. 个人简历

