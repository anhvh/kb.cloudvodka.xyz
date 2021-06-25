---
layout: post
title: Hướng dẫn tạo Bot trên Telegram
tags: [Katex, Markdown]
---


# Hướng dẫn tạo Bot trên Telegram

Để gửi cảnh báo qua telegram bạn cần có  `bot telegram`.

## 1. Tạo bot telegram

Để tạo bot bạn click https://telegram.me/BotFather. Tiếp theo click vào `SEND MESSAGE`.

<img src=https://i.imgur.com/BGuj7iz.png>

Màn hình hiện ra, tiến hành tạo Bot telegram như hướng dẫn sau:

<img src=https://i.imgur.com/cvK73Ws.png>

```sh
/newbot
```
Đặt tên cho Bot telegram. Giả sử tên của Bot là: `petcuatoi`

<img src=https://i.imgur.com/rfkJQj5.png>

Đặt username cho Bot telegram. Giả sử username của Bot là: `petcuatoi_bot`. Lưu ý username phải là chữ thường và phải được kết thúc bằng `bot` ví dụ: `petcuatoi_bot`

<img src=https://i.imgur.com/MdK9FaP.png>

Sau khi tạo xong kết quả sẽ trả về một chuỗi các ký tự. Nó là token của bot. Ví dụ dãy token sẽ là
```sh
1650963056:AAEMR4fLxeQKj7sYzqWeWvY1bnejMM27RdM
```

***Lưu lại chuỗi token này để khi báo khi gửi cảnh báo***

## 2. Lấy thông tin nhận cảnh báo

Để có thể nhận được cảnh báo về telegram của bạn thì bạn cần phải có ID telegram của bạn. Để lấy được ID bạn vào **chat** bất kỳ thông tin gì vào bot telegram của bạn

Tìm kiếm Bot vừa tạo băng username tạo ở trên -> Chọn Start để gửi tin nhắn. Hoặc truy cập vào đường link sau để gửi tin nhắn `https://telegram.me/petcuatoi_bot`

<img src=https://i.imgur.com/z7wWHaj.png>

Truy cập vào địa chỉ sau để lấy ID Chat. Trong đó `$TOKEN` là dãy token của Bot đã tạo ở trên

https://api.telegram.org/bot$TOKEN/getUpdates

Ví dụ với TOKEN trên sẽ là: `https://api.telegram.org/bot1650963056:AAEMR4fLxeQKj7sYzqWeWvY1bnejMM27RdM/getUpdates`

Gửi tin nhắn

<img src=https://i.imgur.com/WArJCRl.png>

Thực hiện F5 lại đường dẫn trên, kết quả trả về như sau:

<img src=https://i.imgur.com/UutTozP.png>

Trong đó:
- 645542801: ID Chat. ID này sẽ lưu lại để nhập vào thông tin nhận cảnh báo.
