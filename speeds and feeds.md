## Table Of Content
* [Intoduction](#intoduction)
* [The Challenge Description](#the-challenge-description)
* [Hint](#hint)
* [Solving It](#solving-it)
* [The Flag](#the-flag)

## Intoduction
This one was my favorite challenge out of all of the challenges in this competition.

I had to use some of my experience with 3D printing and the 3D printer's file formats.

## The Challenge Description
```
There is something on my shop network running at nc mercury.picoctf.net 33596, but I can't tell what it is. Can you?
```

## Hint
```
What language does a CNC machine use?
```

## Solving It
When we netcat that adress, we get back strange content:
```
$ nc mercury.picoctf.net 33596
G0X199.0345Y2.2069
G1Z0.1
G1X198.4828Y1.6552
G1X198.4828Y1.1034
G1X198.7586Y0.5517
G1X199.0345Y0.2759
...and so forth
```
Let's think back to our hint, what is a CNC machine?

After googling it, we find that a CNC machine is some kind of an industrial 3D printer that uses *G-Code*.
When googling G-Code, we see it's the code we recieved from the netcat above, this code will probably build out the flag.

We need to search for a program/site that can run G-Code and preview its content to us.
I found the site [NCViewer](https://ncviewer.com/) that can run the G-Code and display it on a 3D plane.

After saving the netcat's content into a file, I copied the G-Code from the file I created using xclip.
```
$ nc mercury.picoctf.net 33596 > lol.txt
$ xclip -sel c < lol.txt
```
Then, I pasted it into ncviewer and got this image/3D model (**amazing**):

![image](https://user-images.githubusercontent.com/59180254/120991386-3f849580-c78a-11eb-8d67-44e6207a46e1.png)

## The Flag
After typing out the flag: ***picoCTF{num3r1cal_c0ntr0l_e7749028}***

