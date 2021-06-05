First, we are presented with a .jpeg file. A picture of a cat.

![cat](https://user-images.githubusercontent.com/59180254/120892182-a3398200-c615-11eb-826c-687ade79add4.jpg)

The hint for this challenge was: "Look at the details of the file".
So, the first thing I thought of was to look at the file's exif data.

I used [this](https://www.exifdata.com/exif.php) site to check the data (you could also use exiftool but I was lazy).

We get this information

![image](https://user-images.githubusercontent.com/59180254/120892253-06c3af80-c616-11eb-8561-8b4ddb807d0f.png)

The license data seemed suspicious, so I put it in [CyberChef](https://gchq.github.io/CyberChef/#recipe=Magic(3,false,false,'')&input=Y0dsamIwTlVSbnQwYUdWZmJUTjBZV1JoZEdGZk1YTmZiVzlrYVdacFpXUjk)
and got the flag using the magic option (which was awesome to see in action).

The flag - picoCTF{the_m3tadata_1s_modified}	
