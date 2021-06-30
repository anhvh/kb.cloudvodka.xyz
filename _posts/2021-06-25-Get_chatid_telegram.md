---
layout: post
title: Hướng dẫn lấy chatid trên Telegram
tags: [Katex, Markdown]
---

# Hướng dẫn lấy chatid trên Telegram

## 1. Hướng dẫn lấy chatid

Để gửi cảnh báo qua telegram bạn cần có  `bot telegram`.

- Truy cập vào đường link sau: https://telegram.me/myidbot => Chọn ***Send Message***

![](/images/img-telegram/Screenshot_001.png)

- Nhập vào đoàn sau để lấy `chatid`:

```sh
/getid
```

Kết quả trả về như sau:

![](/images/img-telegram/Screenshot_002.png)

## 2. Hướng dẫn lấy groupid

Tạo Group Telegram thực hiện add Bot Telegram gửi cảnh bảo và những user nhận cảnh bảo vào Group. Thực hiện add Bot` @myidbot` để lấy `groupid`

![](/images/img-telegram/Screenshot_003.png)

Thực hiện lấy `groupid` như sau: Nhập vào đoàn sau để lấy `groupid`:
```sh
/getgroupid@myidbot
```
Kết quả trả về như sau:

![](/images/img-telegram/Screenshot_004.png)