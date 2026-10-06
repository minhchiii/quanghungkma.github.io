---
Title: Phishy Lab [Cyberdefender Medium]
draft: "false"
---

## Scenario:

A company’s employee joined a fake iPhone giveaway. Our team took a disk image of the employee's system for further analysis.  
As a soc analyst, you are tasked to identify how the system was compromised


### Q1: What is the hostname of the victim machine?

Trong hệ điều hành Windows, thông tin về tên máy (`Hostname`) được lưu trữ trong Registry tại đường dẫn: `SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName`

Trước tiên ta vào FTK Imager, tiến hành trích xuất file Registry hive `SYSTEM` nằm ở thư mục: `C:\Windows\System32\config\SYSTEM`
![[Pasted image 20261006224049.png]]

Sau đó vào Registry Explorer rồi xem file này
![[Pasted image 20261006224057.png]]

Hostname: ==WIN-NF3JQEU4G0T==

### Q2: What is the messaging app installed on the victim machine?

Trước tiên mình ngó qua thư mục Program Files, để xem xem app có ở đây ko
![[Pasted image 20261006224105.png]]
Kết quả ko thấy app nhắn tin nào, vậy app nhắn tin đấy không được cài đặt cho tất cả người dùng

Đảo mắt qua 1 vòng trong thư mục Users, thấy có mỗi thư mục của User Semah -> tiến hành tìm thử 

Trong thư mục Downloads của Semah, có tồn tại file này
![[Pasted image 20261006224111.png]]


Answer: ==Whatsapp==


### Q3 The attacker tricked the victim into downloading a malicious document. Provide the full download URL.

Lừa đảo thì thường 

![[Pasted image 20261006224124.png]]

![[Pasted image 20261006115121.png]]
==Answer: http://appIe.com/IPhone-Winners.doc ==

## Q4: Multiple streams contain macros in the document. Provide the number of the highest stream.

![[Pasted image 20261006224139.png]]

![[Pasted image 20261006224145.png]]
### Q5
![[Pasted image 20261006224153.png]]
![[Pasted image 20261006224158.png]]
### Q6: The macro downloaded a malicious file. Provide the full download URL.
Answer: ==http://appIe.com/Iphone.exe ==

### Q7: Where was the malicious file downloaded to? (Provide the full path)
Answer: ==C:\Temp\IPhone.exe==