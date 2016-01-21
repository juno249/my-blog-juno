title: Hướng dẫn tạo Blog với Node.js và Hexo
tags:
  - Blog
  - Hexo
  - Node.js
  - junonguyen
categories:
  - Development
  - Node.js
date: 2016-01-18 23:34:00
thumbnail: https://raw.githubusercontent.com/hexojs/logo/master/hexo-logo.png
---
Ở bài viết này, mình sẽ hướng dẫn các bạn tạo một Blog cá nhân một cách nhanh chóng và tiện lợi bằng cách sử dụng Hexo.

Cài đặt
-----
```javascript
$ npm install hexo-cli -g
$ hexo init <Your-blog-name>
$ cd hexo-blog
$ npm i
```
Ngoài ra, bạn có thể chọn lựa cho mình những Themes yêu thích tuỳ ý [ở đây](https://github.com/hexojs/hexo/wiki/Themes).

Cấu hình cho Blog
------
```javascript
$ git clone https://github.com/kywk/hexo-theme-casper.git themes/casper
```
Ở đây, tôi chọn theme Casper theme.
Bên cạnh đó, hãy cấu hình lại file `_config.yaml` để thay đổi giao diện mình đã tải về ở phía trên.

```javascript
# Extensions
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
theme: casper
```
Khởi động lại hexo server để thưởng thức giao diện mới:
```javascript
$ hexo server
```
Ngoài ra, bạn có thể tự thiết lập những thông tin cơ bản cho trang web của bạn thông qua file `_config.yaml` :
```javascript
# Site
title: Juno Nguyen's blog
subtitle: This is my first blog
description: This blog created by using Hexo
author: Juno Nguyen
language: en
timezone: Europe/Volgograd
```
Danh sách [timezone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

Tạo một Post
----
Những post của Blog được viết bằng ngôn ngữ [Markdown](https://en.wikipedia.org/wiki/Markdown) - ngôn ngữ được dùng phổ biến và yêu thích bởi các lập trình viên hiện nay.

```javascript
$ hexo new post "My First Post"
```

Post sẽ được tự động tạo theo đường dẫn sau `source/_posts/My-First-Post.md` :
```javascript
title: My First Post
date: 2016-01-20 12:43:41
tags:
---

blah blah blah

### I can

## Write

In markdown

**ohhhh right***
```
Deploy Blog vào Github
-----
Trước tiên bạn cần tải về project của mình `hexo-deployer-git`:
```javascript
$ npm install hexo-deployer-git --save
```
Bạn cần phải thiết lập đường dẫn đến địa chỉ lưu Blog của bạn trên Github ở file `_config.yml`:
```javascript
# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: git@github.com:juno249/my-first-blog.git
  branch: gh-pages
```
Làm sao để redeploy?

```javascript
$ rm -rf .deploy_git
$ hexo deploy
```
