This one is straightforward, we get a screen with 2 buttons - "choose red" and "choose blue".

![image](https://user-images.githubusercontent.com/59180254/120807056-37411600-c550-11eb-8c87-3ed39f22c0e8.png)

From the name of the challenge, we can guess it's about a HEAD request.

This we can simply do with a curl command -> curl -I http://mercury.picoctf.net:28916

  And we get the flag with a response back:
  
HTTP/1.1 200 OK

flag: picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}

Content-type: text/html; charset=UTF-8
