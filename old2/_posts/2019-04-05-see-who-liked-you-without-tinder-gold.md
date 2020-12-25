---
layout: post
title: See who liked you without Tinder Gold
comments: true
tags: [tinder]
---

#### Result
Images of people who liked you at 640x800, 320x400, 172x216 without Tinder Gold.

![](../../../assets/img/result.png)  	

<br>

#### So
Tinder likes without Gold comes up like this, a blur effect on the photo(s).

![](../../../assets/img/tindergold.png)  	
Initially, I thought that the blurred images were sent from their servers itself.
A simple inspection on the code
```html
-webkit-filter: blur(8px)
filter: blur(8px)
```
Okay, so they are applying a blur effect with CSS. Disabling this would give me a raw image of 172x216 dimension. Exploring media items, the recently liked (only one) would be of 320x400 dimension. 

```html
https://preview.gotinder.com/18d6e533-c874-48ad-ac66-ae6b63aa77fb/172x216_c77f0e5c-40b4-4af4-9b68-5f0ff26ead90.jpg
```
The 172x216 in the URL is the dimensions. Changing it to 320x400, would give me an image of that dimension. 
All the images were coming from the same endpoint. So, I tried changing it to random dimensions with the same aspect ratio which like I guessed didn't work because they were not storing (x dimension) in their server. 

![](../../../assets/img/error.png)



Also, noticed that my profile picture was of better quality.

![](../../../assets/img/profile.png)

To my surprise, that too was coming from the same endpoint. So, now I know that Tinder stores images in 640x800 also. 

So, that's that.