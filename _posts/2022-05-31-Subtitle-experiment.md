---
title: AR Translation Proof of Concept
description: I made a proof of concept of live translating next to your face in AR
featured_image: "/Resources/subtitle/GoogleIOAR.jpg"
---
*Image credit Google*

In the Google I/O conference last month, Google finished off their keynote with some AR "magic". They showed some AR glasses with the ability to allow people to communicate with each other through a language barrier.

[Google AR Glasses](https://www.youtube.com/watch?v=SQd394a4qEo)

The person would speak and some subtitles appear next to their head. The subtitles could be translated, allowing the wearer to understand the previously unintelligble moonspeak though the use of technology. I got excited about this, I don't know any languages other than English, and suddenly technology is making up for my deficiencies. Then I had a think about it and realized, hey, this isn't that special, we can do this on phones today.

<iframe width="800" height="650" src="https://player.vimeo.com/video/715955713" frameborder="0" allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>

So for this proof-of-concept, there are 3 main technologies in play: Speech Recognition, Translation, and Augmented Reality. I'll give a bit of an overview and how they came together for this demo. The crazy thing is, this is all able to work straight on-device, I don't need to send anything through the interwebs to be churned though by supercomputers, this is being done on a mobile chip.

### Speech Recognition
![Siri logo](/Resources/subtitle/Siri_logo.png)

For speech recognition, I'm using the same tech that powers Siri on the phone. Apple provide a framework called `Speech`, which has been available since iOS 10 but in iOS13, we have the ability to do it all on device. I'm surprised at how quick it is, but as you can see, it sometimes has hiccups. If you want to get in-depth on it, I modified some code from one of Apple's sample apps [here](https://developer.apple.com/tutorials/app-dev-training/transcribing-speech-to-text) to do live transcribing of speech into text.

There are some smarts in this, you can see it trying to adjust the text as it thinks. But the smarts are limited, for example, it can't transcribe grammar. I'm cheating a little in adding stops at the end of pauses, if speaking is paused for 2 seconds, it will auto-add a period because I'm making an assumption that people will generally spit out sentences at a time before pausing. In order to add grammatical smarts, we'd have to train and add a machine learning model to recognize sentences. I can only imagine how difficult it must be to add commas and question marks.


### Translation
![Google MLKit logo](/Resources/subtitle/hero_480.png)

Since iOS14, iOS has the ability to do translations on-device via their Translate app. Unfortunately they have not yet made this framework available to developers. However, Google provides this through their [MLKit framework](https://developers.google.com/ml-kit). I'm able to download the needed language files in the app (I skipped that part in the demo) and have them ready for quick translations. It's pretty easy to use. In my demo, when it detects the 2-second pause and ends the sentence, I translate the subtitled string and add it to the log below.

The drawback is that translation is still a little wonky. There are still grammatical smarts that need to be figured out. Just try the Google Translate app and if you know the second language, you can see it's a bit off. I tested it with a coworker who spoke Russian and she mentioned the words were out of order since it was translating the words literally. "I love you" becomes "I you love" in Russian for example. When I checked Korean translations with my mom, she was saying the translations oscillated between being really formal to being almost rude in their casual-ness.

### Augmented Reality

The juicy part of this stack! This was the most exciting for me. If I'm being perfectly honest though, it was probably the most unnecessary. The app probably works better if I just showed the text at the bottom of the screen. In fact, Apple are releasing an app later this year called [Live Captions](https://www.apple.com/au/newsroom/2022/05/apple-previews-innovative-accessibility-features/) that subtitles spoken speech, it just shows the text at the top of the screen. This is one of the pitfalls of AR on the phone: does it really make a better experience than just shoving a label, map, 3D render, etc on good old 2D space? Which is why this is a proof-of-concept and not a real app I'm trying to release on the App Store.

With that out of the way, where this really shines is in context of Google's presentation: if we had AR glasses on our faces. For this demo, I'm using an open-source project I made and had posted about [previously](https://arplaykit.com/tools/2019/02/05/hello-world/) `UIViewControllerNode` where I can make a standard UIView float in AR. In order to use this, I need to use ARKit+SceneKit vs the easier-to-use RealityKit because RealityKit does not give me the advanced material controls that SceneKit can. I'm using face detection and simply making the panel stick to floating a few centimeters to the side of my head, pretty simple!

![AR Face mask](/Resources/subtitle/IMG_2C56AA8D3965-1.jpeg)

When  I turned my head, the panel was obscuring my face so I decided to try and add some occlusion to make the demo look a little better. If I had stayed with RealityKit, I would get this almost for free. RealityKit does lots of neat things with figuring out 3D meshes in the real world using either the FaceID sensors or the LiDAR sensor on the back and determining what goes in front of what. In ARKit-land, we have to do all that manually. In the demo, I followed a tip from Apple's sample code to take the face mesh and render it before the panel. If I throw out the color it looks invisible but will block the panel if my face is in front. In the above screenshot, I turned the white color back on so you can see what the face mesh looks like. It isn't full coverage, the face mesh is only in the shape of a mask, so in the video you can kind of see it slice through my face and behind my eyeballs if I turn my head a certain way. Creepy, huh?

I'm really excited to see what new AR goodies comes in Apple's WWDC conference next week. Maybe the Translations SDK will finally be made available. Maybe the long-awaited AR goggles will arrive? At the very least, I am hoping for some great enhancements to ARKit and RealityKit to continue the train of great AR content that we've seen in the last few months from Meta, Google, and Niantic.
