Title: Alluring Bytes

Description:
```
"Magic is alluring." ~ Grand Pabbie

Buck, Chris, and Jennifer Lee. Frozen II. Walt Disney Studios Motion Pictures, 2019.

Author: Jodie
```

Given file: [alluring.jpg](https://github.com/Coder-Here/HACK-AC-2022-CTF/blob/main/Forensics/Alluring%20Bytes/alluring.jpg "alluring.jpg")

Given hints: you may need a special editor to work magic on the bytes, some magical beings have tails while others don't

Normally opening the image will show us error.

So open the image file in HxD editor so that we can work with the bytes.

![image](https://user-images.githubusercontent.com/63996033/199149487-414e9c27-3c37-4a8a-84cd-5a617d3247e6.png)

The first few bytes indicate that it is the .jpg format. Let's check the ending.

![image](https://user-images.githubusercontent.com/63996033/199149596-8c868ca3-6013-4f51-adae-322e52126599.png)

Ah, IENDB ending is for png files. That means this could be a png file, not a jpg file. So we need to change the first line of bytes from .jpg to .png format. I will download a png picture from online to get the first line of bytes.

![image](https://user-images.githubusercontent.com/63996033/199149865-69db424a-d7db-4bcb-aaa0-f2ffb5b4fc0a.png)

The PNG IHDR opening is only for png. Lets copy them bytes into the alluring.jpg

![image](https://user-images.githubusercontent.com/63996033/199149938-03e34d62-eb3d-4ea8-b058-54cd0bb365d2.png)

Save it and rename it to alluring.png and open the picture normally now.

![image](https://user-images.githubusercontent.com/63996033/199150079-a18fe0cb-3fbe-447d-b192-eaf6767d0353.png)

We got our flag.

Flag: ACSI{w1th0ut_y0u_sh3_m4y_l05e_h3r5elf}
