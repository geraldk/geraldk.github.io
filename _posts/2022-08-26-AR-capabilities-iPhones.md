---
layout: post
title: AR capabilities in iPhones
categories:
- Analysis
excerpt: |
    Comparing the AR capabilities of different iOS devices
feature_image: "/Resources/iphones-ar/title.jpg"
---

iPhones since the iPhone 6S are able to do Augmented Reality. That is 7 generations of iPhones up to the current date, each with different hardware capabilities that is able to do AR differently. On the upcoming iOS 16, we are also in the 6th iteration of ARKit: ARKit 6. With such a wide array of possibilities, I had a hard time finding which iPhone could do what. So today I wanted to break down what hardware is able to take advantages of what capabilities of ARKit. Most of this information is contained within the developer documentation for each capability, so I've tried to condense it into a quick chart.

![Apple SoC schematic](/Resources/iphones-ar/Apple_M1_simplified_schematic-2.jpg)

*Image credit Apple*

## The Neural Engine

The neural engine was introduced in the Apple A11 Bionic SoC, which first debuted in the iPhone 8 and X. It's basically a set of specialized cores that are dedicated to AI operations and machine learning tasks. Previously, the GPUs were used to do this but this allowed for more efficient and powerful applications of machine learning. The first Neural Engine in the A12 Bionic only had 2 cores that were capable of 600 billion operations per second. At the time of writing, the latest Apple SoC, the M2, has a 16-core Neural Engine capable of 15.8 trillion operations per second. With AR applications, there is quite a bit of machine learning needed to do things like predict planes, occlude people, and classify surfaces.

![TrueDepth camera array](/Resources/iphones-ar/trueDepth.png)

*Image credit Apple*

## The TrueDepth camera

Debuting in the iPhone X, the TrueDepth camera is what enables FaceID by using structured light 3D scanning to figure out depth and shapes. Basically it's firing infrared laser beams to map your face which is why you can still use FaceID in dim light. While this technology is low-powered enough to fit in a phone, it has a limited range, hence it's main use in AR is for facial tracking. Face tracking used to be limited to devices with a TrueDepth camera but since iOS 14, it has been expanded to any device with a Neural Engine. I don't have access to any of those devices so am unable to comment on how good it is.

![Lidar in RoomPlan](/Resources/iphones-ar/lidar-roomplan.png)

*Image credit Apple*

## The LiDAR scanner

First introduced in the 4th generation iPad Pro (2020), the LiDAR scanner is integrated into the camera array in the back of iOS devices that include them. Unlike the Neural Engine, which is included in every device that carries the chip, the LiDAR scanner is currently only available in "Pro" devices such as the iPhone 12 Pro, iPhone 13 Pro, and iPad Pros released since March 2020. It's similar to the sensors used in the TrueDepth sensors used for FaceID but with longer range up to 5m and designed to be used for the back camera.

So with these technologies, let's look at a quick breakdown of what devices fall into which categories:

#### Does not support AR: Any device that uses a SoC older than the A9
Anything older than 2014. Devices included are any iPhone 6 or older, any iPad 4th generation or older, iPad Air 2 or older, and iPad Mini 4th generation or older.

#### Category 1: No Neural Engine, no TrueDepth, no LiDAR. 
Roughly TouchID devices from 2015-2017. Devices included are the iPhone 6S, 7, and SE (1st generation) and the iPad (5th generation to 7th generation), iPad Pro (1st generation and 2nd generation).

#### Category 2: Neural Engine, no TrueDepth, no LiDAR.
Basically any TouchID device after 2018. Devices included are the iPhone 8, 8 Plus, iPhone SE (2nd and 3rd generation), iPad (8th generation and newer), iPad Air (3rd generation), iPad Mini (5th generation).

#### Category 3: Neural Engine, TrueDepth, no LiDAR.
Most non-Pro FaceID devices after 2018. Devices included are the iPhone X, XR, XS, XS Max, 11, 12, 13. iPad Pro (3rd generation), iPad Air (4th generation and newer), iPad Mini (6th generation and newer).

#### Category 4: Neural Engine, TrueDepth, LiDAR.
Most Pro devices after 2020. Devices included are the iPhone 12 Pro, 13 Pro and the iPad Pro (4th generation and newer).

I'll group these into different supported AR experiences: Plane detection, facial AR, body tracking, people occlusion, object occlusion, and room scanning. When using these features in an app, you would typically check to see if the user's device supports it in code, for example `if ARFaceTrackingConfiguration.isSupported == true`. In addition, through testing, I've found additional situations where certain capabilities are almost unusable.

| Categories       | 1 | 2  | 3 | 4 |
|------------------|---|----|---|---|
| Plane detection  | ✅ | ✅  | ✅ | ✅ |
| Facial AR        | ❌ | ✅  | ✅ | ✅ |
| Body Tracking    | ❌ | ✅* | ✅ | ✅ |
| People occlusion | ❌ | ✅  | ✅ | ✅ |
| Object occlusion | ❌ | ❌  | ❌ | ✅ |
| Room scanning    | ❌ | ❌  | ❌ | ✅ |
| Wall scanning  | ❌ | ❌  | ❌ | ✅ |
| Geo Tracking    | ❌ | ✅* | ✅ | ✅ |
_*: Needs a little more machine learning power so it needs a Neural Engine in A12 SoCs and newer. That excludes the iPhone 8, 8 Plus, and X._

I added wall scanning, which probably ties in closely to Apple's decision to limit the new RoomScan feature in iOS16 to LiDAR devices. First of all, here's a video I made with my test devices:
- iPhone 7: A Category 1 device
- iPhone 11 Pro: A Category 3 device
- iPhone 13 Pro: A Category 4 device

<iframe width="800" height="650" src="https://player.vimeo.com/video/743319472" frameborder="0" allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>

The problem with wall tracking is that many houses walls are blank featureless slates of a single color (sometimes floors are like this too). With only a camera and not much else in view, the device cannot figure out how far away this featureless slate is and isn't able to detect feature anchors. Hence why the iPhone 7 and 11 Pro struggled to place the plane in the video. Neither had issues finding the poster because it had texture. You can tell the iPhone 11 Pro, with it's machine learning smarts, was able to see part of the wall when it saw a shadow, and then when it recognized the poster. But when the 13 Pro with it's LiDAR came into play, it saw the wall straight away and was able to classify it immediately.

There is yet one more AR feature that is selective but it depends less on your device capabilities and more where you live: AR geotracking. As of writing, only selection cities in the US, Australia, Canada, Japan, Singapore, and Canada support this feature where the Apple Maps team have pre-scanned cities with LiDAR so that you can place objects on the train station for example. The latest list of supported cities is [here](https://developer.apple.com/documentation/arkit/argeotrackingconfiguration). In addition, the hardware needed is an A12 or newer (similar to body tracking).

Besides capability requirements, having a more powerful processor and better scanners affects the experience. I made another video of an easy scenario on my balcony. It has daylight conditions (even though it's cloudy) with textured objects and a task of simply finding planes. Even Category 1 devices like my iPhone 7 can do this.

<iframe width="800" height="650" src="https://player.vimeo.com/video/743323813" frameborder="0" allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>

You can see that the iPhone 7 is able to pick up the surfaces on the highly textured box quickly but takes a little while to find the less textured tile floor. 
The iPhone 11 Pro is able to pick up the floor almost right away and even recognizes the top of the box in the reflection behind it after some coaxing.
The iPhone 13 Pro picks up everything almost instantly and even the reflections of the floor and box a second later.
