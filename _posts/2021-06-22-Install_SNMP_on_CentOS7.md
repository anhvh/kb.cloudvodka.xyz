---
layout: post
title: Giám sát sử dung SNMP
tags: [Katex, Markdown]
---
# Giám sát sử dung SNMP

SNMP (Simple Network Manager Protocol) là giao thức rất phổ biến trong môi trường network hiện nay, hầu hết các thiết bị mạng đều hỗ trợ SMNP. Zabbix từ lâu cũng đã tích hợp monitor hệ thống qua giao thức SNMP.

Trong hướng dẫn này, sẽ hướng dẫn monitor Windows Server thông qua SMNP. 

## 1. Mô hình triển khai

## 2. Cài đặt và cấu hình SNMP trên CentOS7

- Cài đặt các gói sau:
```sh
yum -y install net-snmp net-snmp-utils
```
- Chỉnh sửa file cấu hình `/etc/snmp/snmpd.conf` như sau:

```sh
$ cp /etc/snmp/snmpd.conf /etc/snmp/snmpd.conf.org
$ vim etc/snmp/snmpd.conf
...
rocommunity  public
syslocation  here
syscontact  root@localhost
...
view    systemview    included   .1.3.6.1.2.1.1
view    systemview    included   .1.3.6.1.2.1.25.1.1
view    systemview    included   .1
view    systemview    included   .1.3.6.1.4.1.2021.4.3.0
view    systemview    included   .1.3.6.1.4.1.2021.4.4.0
view    systemview    included   .1.3.6.1.4.1.2021.4.5.0
view    systemview    included   .1.3.6.1.4.1.2021.4.6.0
view    systemview    included   .1.3.6.1.4.1.2021.4.11.0
view    systemview    included   .1.3.6.1.4.1.2021.4.13.0
view    systemview    included   .1.3.6.1.4.1.2021.4.14.0
view    systemview    included   .1.3.6.1.4.1.2021.4.15.0
view    systemview    included   .1.3.6.1.4.1.2021.11.9.0
view    systemview    included   .1.3.6.1.4.1.2021.11.10.0
view    systemview    included   .1.3.6.1.4.1.2021.11.11.0
...
```
`rocommunity` là thông số quan trọng như là một cái key để liên lạc giữa cliet và server. Chuỗi SNMP community giống như passowrd dùng để thiết lập mối quan hệ giữa server monitor và agent, do đó chúng ta cần khai báo chuỗi SNMP community để monitor có thể truy vấn thông tin từ switch.

- Mở Port trên Firewalld

```sh
firewall-cmd --permanent --add-port=161/udp
firewall-cmd --reload
```
- Restart service
```sh
systemctl enable snmpd
systemctl restart snmpd
```
## Tài liệu tham khảo
- https://github.com/domanhduy/zabbix-monitor/blob/master/Add%20host%20s%E1%BB%AD%20d%E1%BB%A5ng%20SNMP.md
