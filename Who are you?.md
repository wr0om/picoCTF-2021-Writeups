This one is in the web exploitation category and requires tinkering with the packets sent to the site given.
This we can do manually with the curl command or with a proxy like Burp Suite.

First, we are presented with the message: "Only people who use the official PicoBrowser are allowed on this site!"

We can guess that we just need to change the user agent header to "PicoBrowser" - and it works.
*User-Agent: PicoBrowser*

![Capture](https://user-images.githubusercontent.com/59180254/120638805-486b2380-c479-11eb-8091-05a9e0d2256a.PNG)

Second, we are presented with the message: "I don't trust users visiting from another site."
We can change the Referer header (yes with 1 r) to the website itself - and it works.
*Referer: http://mercury.picoctf.net:34588*

Next, we get the message "Sorry, this site only worked in 2018.".
We can change the time and date of the request with the Date header.
*Date: Tue, 15 Nov 2018 08:12:31 GMT*

Then, we get the message "I don't trust users who can be tracked."
We can use the DNT (Do Not Track) header to fix this issue.
*DNT: 1*

This one tricked me for some time, I tried all kinds of different methods to solve this.
We get the message "This website is only for people from Sweden."
To fix this issue, we need to use the X-Forwarded-For header that changes the IP that the site receives - we need to find an IP in sweden (just google it).
*X-Forwarded-For: 31.15.63.255*

Finally, we get this message "You're in Sweden but you don't speak Swedish?"
This one's easy, you have to change the Accept-Language header, if you look online you can find the shortcut for the Swedish language code - sv-SE.
*Accept-Language: sv-SE*


Final request (in Burp):
GET / HTTP/1.1
Host: mercury.picoctf.net:34588
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: PicoBrowser
Referer: http://mercury.picoctf.net:34588
Date: Tue, 15 Nov 2018 08:12:31 GMT
DNT: 1
X-Forwarded-For: 31.15.63.255
Accept-Language: sv-SE
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: close

In a curl command:
curl -i -s -H "Accept: application/json" -H "Content-Type: application/json" -H "User-Agent: PicoBrowser" -H "Referer: http://mercury.picoctf.net:34588" -H "Date: Tue, 15 Nov 2018 08:12:31 GMT" -H "DNT: 1" -H "X-Forwarded-For: 31.15.63.255"  -H "Accept-Language: sv-SE" http://mercury.picoctf.net:34588/ | grep pico

Then, we get the flag - picoCTF{http_h34d3rs_v3ry_c0Ol_much_w0w_79e451a7}

![image](https://user-images.githubusercontent.com/59180254/120639072-a435ac80-c479-11eb-80bd-bd8d559fbdd5.png)








