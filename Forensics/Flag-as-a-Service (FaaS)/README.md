Title: Flag-as-a-Service (FaaS)

Description:
```
Recently, I've learnt of this new cloud business model to earn MORE money FAST! 
They claim to be powered by blockchain with a fully AGILE WATERFALL. 
Anyways, I stole one of their lead developers phone to earn some money for myself, but I couldn't make sense of the data. 
Can you help me to steal their business plan?

MD5: f88c2662cc8f9ef1cb62c11af3b6733c

Author: Sean
```

[MEGA mirror](https://mega.nz/file/KY40QTJC#PHe21W4jZlbismSR3_FCLs0TmRrzy9Ys1VbXt_w-1Yw)

[Google drive mirror](https://drive.google.com/file/d/1zf8o08evtCDJnyF-kVewfFpNHFsUgpWA/view?usp=sharing)

Given hint: Is there a way to find SMS messages? Search up mobile/android forensics on google.

Caution: File is 6GB big. Make sure you have enough space

When I dowloaded the big file, it was in the .img format. I searched online for Anriod img file opener and came across this [FTK Imager](https://go.exterro.com/l/43312/2022-08-23/f7rytx). Quickly downloaded it and opened the file in it.

![image](https://user-images.githubusercontent.com/63996033/199923130-cc5371c4-2369-45ac-8aab-98f7c340065f.png)

![image](https://user-images.githubusercontent.com/63996033/199923147-66c59fb3-580a-4338-ab85-4fafd562fb1b.png)

![image](https://user-images.githubusercontent.com/63996033/199923243-d9693ca2-2a67-4905-bd38-b1d523487195.png)

![image](https://user-images.githubusercontent.com/63996033/199923270-9da9414b-4749-4c29-8c15-2c03b0959c22.png)

In the description it says about SMS messages. We can check all the paths stated [here](https://www.magnetforensics.com/blog/android-messaging-forensics-sms-mms-and-beyond/) for any information

![image](https://user-images.githubusercontent.com/63996033/199924268-512f97b5-5878-4b22-8346-bc2856a53e76.png)

![image](https://user-images.githubusercontent.com/63996033/199924346-99f90a43-a544-4e8f-93d4-5bc7edb599e8.png)

![image](https://user-images.githubusercontent.com/63996033/199924435-40b2592b-3866-4b5d-83ad-9639cf3c5577.png)

There does not seem to be anything here.

![image](https://user-images.githubusercontent.com/63996033/199924571-cedc3c26-93d0-4001-a1fa-94468f380ef5.png)

![image](https://user-images.githubusercontent.com/63996033/199924802-3c266807-632b-469c-91f9-8353ceb5a064.png)

Aha, the next file contains 256 bytes of data in a database file, so it must contain what we need. Lets download the file and open it in a SQLite database viewer.

![image](https://user-images.githubusercontent.com/63996033/199924874-6f83ba6a-fc4a-449a-b366-a7c8ced9970f.png)

![image](https://user-images.githubusercontent.com/63996033/199925122-05b9dbff-84d5-4a01-8c3e-2d798d736849.png)

![image](https://user-images.githubusercontent.com/63996033/199925181-6617886a-6648-4e09-b202-5c1614c45f3e.png)

Open database, locate the file bugle_db and open it.

![image](https://user-images.githubusercontent.com/63996033/199925313-2715b32f-31ae-4c1f-b22b-123b685fb6a4.png)

![image](https://user-images.githubusercontent.com/63996033/199925356-a8b03b60-3a29-4c6a-b23f-97c7bb7145a8.png)

![image](https://user-images.githubusercontent.com/63996033/199925368-1a73eaca-f9b4-47ac-bce7-6b10b7aa93fc.png)

Now we need to find the correct table. Look through all of them and see which table is of interest. Use Browse Data tab.

![image](https://user-images.githubusercontent.com/63996033/199925685-29af4ded-09e8-4fbb-b0b7-680fa2552e47.png)
![image](https://user-images.githubusercontent.com/63996033/199925820-69b694f1-bfc7-45da-93f4-aa4a077e9a5c.png)

Lessgo, we have a conversation going on here. Key points: Flag is encrypted by AES/ECB and the key is ctf_as_a_service and it is stored in the wifi passwords file. Open up the FTK Imager and check [this](https://www.dataforensics.org/wifi-forensics/).

![image](https://user-images.githubusercontent.com/63996033/199926758-cdd7fd1e-ae0a-423f-9c9d-b872b5b44dca.png)

![image](https://user-images.githubusercontent.com/63996033/199926878-1f3f3ff1-cc54-41fb-a16c-cd785e11bf5a.png)

![image](https://user-images.githubusercontent.com/63996033/199926919-e1bfbba7-f017-4fef-aa47-033fd14011da.png)

![image](https://user-images.githubusercontent.com/63996033/199926959-101e71ec-3214-49a8-933f-ed9c397e4079.png)

We can check this file first.

![image](https://user-images.githubusercontent.com/63996033/199927004-41b355e6-7a24-41f8-a4e5-644c62d7e5c2.png)

Could this be the encrypted version of the flag. Lets check [this](https://www.devglan.com/online-tools/aes-encryption-decryption) AES/ECB decoder.

![image](https://user-images.githubusercontent.com/63996033/199927398-35936497-f6ab-486d-8d6d-a784783f56dc.png)

![image](https://user-images.githubusercontent.com/63996033/199927497-84162f0c-4265-4ad0-b45d-6f0bceba28d0.png)

Ayo, maybe lets change the input text format. 

![image](https://user-images.githubusercontent.com/63996033/199927708-5669dd6a-0a5a-407c-bab1-a0b1237ef6ca.png)

![image](https://user-images.githubusercontent.com/63996033/199927872-19db7a85-4cc8-49ce-bce9-8b086e40256e.png)

Ok, looks like base64, just decode it. 

![image](https://user-images.githubusercontent.com/63996033/199927952-27665620-7bbd-4074-9f24-8a56f7ca2e54.png)

Yay, the flag.

Flag: ACSI{w1f1_p4ssw0rd_flAggg}
