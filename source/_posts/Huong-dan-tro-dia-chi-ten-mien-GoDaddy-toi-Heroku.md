---
title: Hướng dẫn trỏ địa chỉ tên miền GoDaddy tới Heroku
tags:
  - GoDaddy
  - Heroku
  - Node.js
  - junonguyen
categories:
  - Development
date: 2016-01-20 00:10:00
---

Bài viết ngày hôm nay mình sẽ hướng dẫn cách bạn trỏ tên miền (domain)  website mua từ [**GoDaddy**](https://godaddy.com/) đến hosting [**Heroku**](http://heroku.com).
Trước tiên, bạn cần kiểm tra xem ứng dụng Web của bạn trên hosting **Heroku** đã tồn tại những domains nào bằng cách:
```bash
$ heroku domains --app <app-name>
```
Câu lệnh trên sẽ trả về danh sách những domains mà bạn đã thiết lập cho ứng dụng Web.
Bạn có thể biết tên những thông tin khác của ứng dụng Web bằng cách:
```bash
$ heroku apps:info
```
Hoặc thêm hoặc bớt domains của ứng dụng Web:
```bash
$ heroku domains:add www.example.com --app <app-name>
$ heroku domains:remove www.example.com --app <app-name>
```
Nào bây giờ hãy thêm domain bạn vừa mua từ Godaddy vào ứng dụng Web:
```bash
$ heroku domains:add www.example.com --app <app-name>
$ heroku domains:add example.com --app <app-name>
```
Ở đây mình thêm cả 2 đường dẫn `www.example.com` và `example.com` để người dùng có thể truy cập trực tiếp vào web của bạn mà ko cần thông qua `www`.

Sau đó, hãy đăng nhập vào [GoDaddy](https://godaddy.com/) để thiết lập cho domain của bạn.
Ở cửa sổ GoDaddy Dashboard, bạn hãy chỉnh sửa CNAME của _www_ trỏ đến subdomain được cấp miễn phí bởi Heroku, ví dụ: `example.herokuapp.com`
![Chỉnh sửa host www trỏ đến submain trên ](http://www.junonguyen.com/assests/img/blog2-img1.png)
Để người dùng có thể truy cập một cách nhanh nhất đến địa chỉ của web của bạn thì trong phần `Setting` chọn `Fowarding` và thêm vào đó domain: `http://www.example.com`, redirect là `301` và loại là `Forward only` như hình:
![Thêm Forwarding cho domain](http://www.junonguyen.com/assests/img/blog2-img2.png)
![Kết quả](http://www.junonguyen.com/assests/img/blog2-img3.png)
Bây giờ bạn có thể truy cập vào web của bạn qua 2 đường dẫn: example.com và www.example.com.
Chú thích
------
https://devcenter.heroku.com/articles/custom-domains