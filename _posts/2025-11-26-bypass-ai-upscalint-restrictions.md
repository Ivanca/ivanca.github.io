---
title: How to Bypass AI's restrictions when upscaling images
date: 2025-11-26 00:00:00
categories:
  - Programming
author_staff_member: ivan-castellanos
image: "/images/ai-bypass.png"
background_image_path: "/images/ai-bypass.png"
large_header: false
---

So the moral police loves to decide what images you can or cannot upscale when using tools like Google Gemini, ChatGPT and so on, I have found that you can (most of the times) bypass such kind of detection by obfuscating the image: By distorting it, upscaling it, then when you get the upscaled image you do the reverse operation on it. This works really well with Google's AI but not so much for ChatGPT, mostly for 3 reasons, 1st: it has stronger detection techniques, 2nd: Frequently crops the image in unwanted ways, 3rd: It frequently hallucinates objects and people that aren't in the original image (despite just asking it to upscale it). So I recommend you use Google's AI nano banana if you want to try this.

But first of all this is all for educational purposes and you are likely better of using other upscaling tools, and I encourage you to not break any legal agreements you may have with any AI company, and if you decide to do so you are responsible for any consequences for doing so.

Back to the image obfuscation: First you need to invert the hue of the image (and I mean just the HUE, not the colors because that involves brightness), in image editing software like Photoshop that means change the hue 180 degrees, after that flip the image vertically, then warp the image but specifically you must use some kind of warp that can be reversed, and also a warp that doesn't make you lose any pixels (e.g. it doesn't push any pixels out the image, only "stretches" them a bit), in Photoshop the perfect warp for this is called wave with a 50% strength, see in action here:

![](/uploads/hitler_hang.gif){: width="563" height="754"}

Doing this process manually with Photoshop or GIMP can be tedious and error-prone so I created a simple website to do this: [https://ivanca.github.io/bypass-gpt/](https://ivanca.github.io/bypass-gpt/)

To be clear this page helps you with the image edition part, you still have to drag and drop the resulting images into the AI prompt and ask it to upscale them, then give those back to the extension, but that should take mere seconds, for best results I suggest to use as prompt "upscale this image, keep the exact same aspect ratio", here is a video showing the whole process:

<video controls>
  <source src="/uploads/bypass-image-ai-detection.mp4" type="video/mp4">
  Your browser does not seem to support the video tag.
</video>

And yes, the process has some rough edges but I will try to get them sorted out soon, I think addind a 2 pixel border that As a final note, I want to mention that ChatGPT itself (codex preview) helped me create this extension and I love the tiny bit of irony in that.

As a even more final note, I want to mention that I'm looking for job  as a Front-end developer (or Full-stack), including freelance opportunities, so if you are interested in any of that you are more than welcome to drop me a line, my email it's the very same name of this blog at gmail dot com. 

