---
title: Hello World
featured_image: "/Resources/Blog1-4.jpg"
---

My first post! I'm primarily a developer that works with UIKit in iOS and I would love to bring some of those elements into the 3D world that ARKit and SceneKit live in. Luckily, it's not that hard! Introducing: `UIViewControllerNode`. It's a pretty simple concept, it's just a `SCNNode` subclass with a `SCNPlane` geometry that is textured with the `UIViewController`'s view. 

{% include button.html text="See it on Github" link="https://github.com/geraldk/ARPKViewController" icon="github" %}

A few extra bits:
- I added the option to have it billboarded so that the view is always visible
- The `viewController` parameter in the init is there so the node will retain the viewController for you. As long as you add it as a child of something or retain it in some other way, the viewController sticks around too

I'm pretty surprised on how interactions work out of the box, you can scroll the tableView in my sample app, even if there are multiple of them. Sometimes it's a bit hard to scroll, I wonder if it's my `UITapGestureRecognizer` interfering with things or something is up with the hit-testing
I have a bunch of ideas on how to use this that I'll be exploring in future posts. In the meantime, feel free to use it yourself!
