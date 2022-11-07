---
title: Thoughts on Meta Connect
description: Some thoughts on the presentations and announcements of Meta Connect 2022
featured_image: "/Resources/metaconnect2022/title.png"
---

Meta's Connect conference was aired on October 11, 2022. They streamed it on Facebook as well as had some of the sessions in Meta Horizon Worlds. The Quest Pro was officially announced as well as an important partnership with Microsoft, a focus on working in VR, and a push to make Meta Avatars your digital identity.

![Quest in the workplace](/Resources/metaconnect2022/workplace.jpg)
*Image credit Meta*

## The workplace in VR

So the Quest 2 is $400 USD and the Quest Pro is $1500 USD. Internally the chip powering them is almost the same. In the dev sessions, they're asking that games be built for Quest 2 as a baseline and on launch list of games for the Pro, all games were compatible with Quest 2 as well. Also, because of the "better" field of view, the performance in games can actually be worse, capped at 90Hz instead of having the option of an experimental 120Hz on the Quest 2. So... who is buying the Quest Pro? This seems to be where Meta is looking to target with the next frontier of VR: the office. The cost has gone into parts of the headset that Meta thinks that will make meetings more engaging: facial tracking, color Passthrough, a compact headset that is comfortable to wear, controllers that can be tracked independently (under desks perhaps). And the big one: their new partnership with Microsoft who has commited to having Microsoft Teams be integrated into Quest, Microsoft 365 (formerly Office 365) be accessible from Quest, and their other cloud-based platforms like Windows 365 and XBox Cloud Gaming in Quest. Funny thing is that I never heard the term "exclusive" used so if some other big tech company came out with a consumer/enterprise level AR/VR headset, Microsoft could be part of that too...
The title image shows people in a meeting room gawking over a 3D model. You can't actually do that yet until next year in Horizon Workrooms. Working with each other virtually and in real-life is a concept they're working on called Magic Rooms, it'll be interesting to how it changes the feeling of working together in VR.


![Meta Avatars](/Resources/metaconnect2022/avatars.jpg)

*Image credit Meta*

## Avatars

After the backlash on social media on how creepy Zuckerberg's Meta avatar was, they tried to show a minimal amount of what the current avatars look like. When Zuckerberg's avatar made an appearance on screen, it was with an experimental, higher resolution avatar. They did have a lot of announcements around said avatars, namely on how they would love for everyone to use Meta Avatars to be their digital representation. They're rolling out uses of Avatars across all their own products: WhatsApp, Instagram, Facebook and are planning on making SDKs available for third-party developers even in iOS and Android. 

![Quest Pro](/Resources/metaconnect2022/questPro.png)

*Image credit Meta*

## Quest Pro
I won't comment much more about the just-announced Quest Pro, there are tons of great reviews and first impressions of people who have [actually](https://www.youtube.com/watch?v=CqkhjL3WvWQ) [tried it](https://www.youtube.com/watch?v=lT1sps72_sE). Personally, I won't be getting it because I only have limited funds and there are interesting developments coming soon. For gaming, the Playstation VR2 sounds really promising. Aside from still being tethered to a cord, it boasts some impressive specs and has the backing of Playstation and its studios. For the office and consumer, Apple will hopefully be coming out with an AR headset next year. In fact, near the end of the Connect keynote, Zuckerberg makes references that Quest is the open platform in contrast to other closed platforms which I believe heavily hints towards the release of Apple's headset.  

## The Connect keynote
First of all, they hyped up being able to "experience" the conference in Horizon Worlds. You can see videos of them [building the "venue" and everything](https://www.oculus.com/blog/meta-connect-horizon-worlds-behind-the-scenes/), kinda cool. I wasn't able to personally experience it for myself since Horizon Worlds is limited to select countries that aren't Australia but I found a video of someone running around it [here](https://www.youtube.com/watch?v=ghqwMTmDk5U). I tried attending Facebook Connect via the Oculus Venues app in 2020 and it seemed pretty similar; sit in a virtual movie theatre with a bunch of other people and watch a 2D screen. Being in VR is extra tiring and the "theatre" was filled with a bunch of kids impatient for the Quest 2 announcement and screaming at the top of their lungs because being online means no social filters. 

![Feedback on Connect](/Resources/metaconnect2022/connectComment.png)

It looks like this year was pretty much the same.

I have to admit, the section with Avatars was pretty cool with prerecorded 3D models moving and talking (you can see an example in the YouTube video [here](https://youtu.be/ghqwMTmDk5U?t=3347) ). I wish they worked on doing that properly for the whole keynote but John Carmack (CTO of Oculus VR) explained some of the technical difficulties of doing that on limited Quest hardware in his talk. But seeing how Epic does it with [concerts in Fortnite](https://www.youtube.com/watch?v=k5EAPwXxcng), I think that it could be a really interesting experience that has the potential to be more enjoyable than attending a conference in person.

![Connect speakers](/Resources/metaconnect2022/connectSpeakers.png)

*Image credit Meta*

## Connect Developer sessions

The sessions themselves talk about new features coming to APIs and in the Quest Pro. I wouldn't necessarily call them "developer" sessions though. The screenshot above shows a typical lineup of speakers. If you look at their job titles, nowhere do you see "Engineer" or "Developer". I had a look at lineups of 8 different sessions and only found 1 with a Meta developer and 1 with a developer from a third-party. Not many designers either. The talks were dominated with Product Managers running through scripted pantomimes and I didn't see any code shown, no technical dives, and barely any sample code. When trying to run the one sample app I found, it was built using an outdated version of Unity and the dependency management was a nightmare to figure out (I eventually gave up). Admittedly, I have hardly any experience with Unity so this may be par the course for an actual Unity app but the hurdle to getting started developing any of this was so high.
I think Meta is trying though and it was good to see that they were making strides with developer tooling. They made some new performance testing tools, automated testing, and their Developer Hub app has some neat features. They're trying to get better at promoting apps in the Store and having third-party developers talk in their conference gives a nice third-party view and shows they don't have their heads stuck in the sand. They announced investment into learning VR with Coursera and Unity. I also really like that they're open and promote the sideloading scene.

## Capabilities of mixed reality

What I was most interested in was the improvements to Passthrough/Presence Platform and what an AR/Mixed reality world might look like. Their updated sample app, The World Beyond, showcases the cutting edge of what Passthrough can do. You can put it on the Quest directly via sideloading on AppLab [here](https://www.oculus.com/experiences/quest/4873390506111025/) or if you're technically inclined, you can try building it onto your device via Unity [here](https://github.com/oculus-samples/Unity-TheWorldBeyond), although trying to detangle dependency management was too frustrating for a Unity beginner like me.

<iframe width="800" height="650" src="https://player.vimeo.com/video/768038873" frameborder="0" allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>
In this first video, I've already mapped my walls, windows, and couch. I'm trying to figure out how to map my coffee table but there are only limited choices so I've had to go with "other". One of the biggest shortcomings I found with Presence Platform is its inability to figure out your room on its own. Before you even start the experience, you need to map out the floor, walls, and even all the furniture in your room which takes a good 10-15 minutes. Only then can the little animated character in the experience run around and interact with your real-world room properly. Part of it is the lack of depth sensors but I think it's also the lack of machine learning firepower. With Niantic's Lightship, Google's ARCore, and Apple's ARKit they've figured out the shape of what's in front of you through tons of machine learning and computer vision magic and use that to do things like object occlusion and with the LiDAR sensor in Pro iPhones, RoomPlan does a really good job of mapping out your room. It's a little disappointing that both the Quest 2 and Quest Pro lack a depth sensor and I think that's really what limits them to your living room or office room. Meta does seem to care about it, they showed off a segment where they worked with Canegie Mellon to help blind people navigate Pittsburg Airport via an app. However the mapping was done with Project Aria headsets, which are the prototype high-spec glasses that Meta's Reality Labs is doing experiments with, I'm guessing they DO have depth sensing and are designed to freely walk around in the real-world with.

<iframe width="800" height="650" src="https://player.vimeo.com/video/768038791" frameborder="0" allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>
In this second video, I'm interacting with the animated character. You can see at one point as she runs behind my couch, she occludes strangely. When I mapped the couch, Presence Platform only considers it a rectangular block, it doesn't actually know it has arms and a back. The character can climb on top of the furniture I mapped and the ball will bounce off them correctly. But the device isn't learning about my room itself, I had to tell it what was in it via a long setup process.

What I really liked was the portal to the virtual world. The character was no longer confined to my small room and could walk "outside". For a few minutes, I could zap away my walls and be in a bigger world. Until I run into the Guardian border that makes sure I don't trip over my coffee table...

## Conclusion
Meta is obviously throwing a lot of money and effort into making VR/Mixed reality/AR a thing. It seems like this year, they're really leaning into mixed reality to try and get us to commit to their vision, especially in the workplace. All of it is still very beta but it's pretty exciting to see glimmers on what the future is like.
