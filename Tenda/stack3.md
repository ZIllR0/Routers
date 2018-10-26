vendor:Tenda

product:AC9 AC7 AC10 AC15 AC18 and so on

version:V15.03.05.19(6318)_CN(AC9), V15.03.06.44_CN(AC7), V15.03.06.23_CN(AC10), V15.03.05.19_CN(AC15), V15.03.05.19(6318)_CN(AC18) and earlier

type:buffer overflow

author:Ming Yuan

institution:NISL@Tsinghua University


Vulnerability description
-------------------------
I found a buffer overflow vulnerability in the router's web server--httpd. While processing the `startIp` and `endIp` parameters for a post request, the value is directly `sprintf` to a local variable placed on the stack, which overrides the return address of the function, causing buffer overflow. The details are shown below:
![image](https://github.com/ZIllR0/Routers/blob/master/Tenda/images/stack5.jpg)
![image](https://github.com/ZIllR0/Routers/blob/master/Tenda/images/stack6.jpg)

PoC
-------------------------

![image](https://github.com/ZIllR0/Routers/blob/master/Tenda/images/stack7.jpg)

This PoC can result in a Dos. 


p.s.Given the vendor's security, we only provide parts of the URL.
