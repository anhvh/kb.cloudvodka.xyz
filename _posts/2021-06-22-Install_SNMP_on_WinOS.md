---
layout: post
title: Giám sát sử dung SNMP trên Windows
tags: [Katex, Markdown]
---

# Giám sát sử dung SNMP

SNMP (Simple Network Manager Protocol) là giao thức rất phổ biến trong môi trường network hiện nay, hầu hết các thiết bị mạng đều hỗ trợ SMNP. Zabbix từ lâu cũng đã tích hợp monitor hệ thống qua giao thức SNMP.

Trong hướng dẫn này, sẽ hướng dẫn monitor Windows Server thông qua SMNP. 


## 1. Mô hình triển khai

## 2. Cài đặt SNMP trên Window Server 2k16

Mặc định trên Windows Server đã có sẵn SNMP service, ta cần làm theo những bước sau để khởi chạy SNMP

- Bật Server Manager 

![](/images/img-zabbix/Screenshot_001.png)

- Chọn Add roles and features

![](/images/img-zabbix/Screenshot_002.png)

- Tìm tính năng SNMP sau đó tích vào ô SNMP Service sau đó ấn Next

![](/images/img-zabbix/Screenshot_003.png)

- Thực hiện cài đặt SNMP và kiểm tra quá trình cài đặt

![](/images/img-zabbix/Screenshot_004.png)

- Kiểm tra xem services đã chạy chưa. Bật cmd của windown, thực hiện lệnh: `services.mcs` tìm dịch vụ SNMP.

![](/images/img-zabbix/Screenshot_005.png)

Dịch vụ đã cài thành công

- Allow thêm một số tính năng cho SNMP trên Windows

Click chuột phải chọn Properties. Trong tab Agent tích hết các mục sau và điền thông tin cần thiết và chọn Apply

![](/images/img-zabbix/Screenshot_006.png)

Trong tab Security cho phép một số connection đến Windows Server thông qua SNMP, sau đó Add và Apply thay đổi

![](/images/img-zabbix/Screenshot_007.png)

Vẫn là tab Security chọn tiếp Accept SNMP packages from any hosts

![](/images/img-zabbix/Screenshot_008.png)


Bước 6: Trên Zabbix Server kiểm tra quá trình cài đặt
Chạy lệnh sau để kiểm tra

snmpwalk -v2c -c <CONTACT_NAME> <IP_WINDOWS_SERVER>
Ví dụ trong bài này sẽ như sau:

snmpwalk -v2c -c cloud365 172.16.4.183
Output như sau là thành công

SNMPv2-MIB::sysDescr.0 = STRING: Hardware: Intel64 Family 6 Model 45 Stepping 7 AT/AT COMPATIBLE - Software: Windows Version 6.1 (Build 7600 Multiprocessor Free)
SNMPv2-MIB::sysObjectID.0 = OID: SNMPv2-SMI::enterprises.311.1.1.3.1.2
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (109184) 0:18:11.84
SNMPv2-MIB::sysContact.0 = STRING: cloud365
SNMPv2-MIB::sysName.0 = STRING: WIN-V2CJOSGSBG3
SNMPv2-MIB::sysLocation.0 = STRING: cloud365
SNMPv2-MIB::sysServices.0 = INTEGER: 79
.......................................


## 3. Thêm host Windows lên Zabbix-Server

- Đăng nhập lên Zabbix Web

- Ta chọn như sau Configuration => Host => Create Host

- Trong màn Create Host, điền tối thiểu các thông số của host như sau

![](/images/img-zabbix/Screenshot_009.png)

- Chọn Template. Chọn Template OS Windows SNMPv2 sau đó Select

![](/images/img-zabbix/Screenshot_010.png)


- Trong tab Macros chọn như sau sau đó chọn Add
Macros: {$SNMP_COMMUNITY}
Value: Agent

![](/images/img-zabbix/Screenshot_011.png)

- Kiểm tra nếu SNMP hiện màu xanh là thành công
