---
title: How to Deal With AI Restrictions When Upscaling Images
date: 2025-11-26 00:00:00
categories:
  - Programming
author_staff_member: ivan-castellanos
image: "/images/ai-bypass.png"
background_image_path: "/images/ai-bypass.png"
large_header: false
---

Modern AI tools—Google Gemini, ChatGPT, and many others—often apply strict content-safety filters when you try to upscale certain images. These systems sometimes misclassify completely harmless images, blocking them from being processed. Through experimentation, I’ve noticed that you can sometimes avoid these false positives by lightly obfuscating the image before sending it to an AI model. After the upscale, you simply reverse the transformation to recover the original look.

In my experience, this works quite well with Google’s AI, but not as reliably with ChatGPT. The main issues I’ve observed with ChatGPT are:

It has stronger and more sensitive detection systems.

It often crops images in unintended ways during the upscale process.

It occasionally hallucinates new objects or people not present in the original photo, even when the prompt is a simple "upscale this image."

Because of this, Google’s smaller “Nano” models tend to be more consistent for this specific experiment.

Before going any further: this article is intended purely for educational and technical exploration. You should always respect the terms of service of any AI platform you use. If you decide to test any technique, you alone are responsible for understanding and complying with the rules of each tool.

### The Image-Obfuscation Technique

The idea is straightforward:
Apply a reversible distortion before sending the image to the AI, then undo the distortion afterward. Through trial and error, the following sequence works well:

Invert the hue of the image (only the hue channel—don’t change brightness or saturation), in Photoshop and other image edition Software this means shifting Hue by 180°.

Flip the image vertically.

Apply a reversible warp—one that doesn’t push pixels out of bounds or permanently distort details, in Photoshop the Wave warp at around 50% strength is great: it stretches pixels without losing any.

![](/uploads/hitler_hang.gif){: width="563" height="754"}

Doing all of this manually in Photoshop or GIMP quickly becomes tedious. To make the experiment easier, I built a small tool:

👉 [https://ivanca.github.io/bypass-gpt/](https://ivanca.github.io/bypass-gpt/)

This page automates the reversible distortion step, you still need to upload the warped version to the AI for upscaling, then return the result to the tool to reverse it—but the whole loop only takes a few seconds.

For best results, use a simple and strict prompt such as:

> Upscale this image, keeping the exact same aspect ratio.

Here’s a video of the entire workflow:

<video controls>
  <source src="/uploads/bypass-image-ai-detection.mp4" type="video/mp4">
  Your browser does not seem to support the video tag.
</video>

I know the current version has a few rough edges, and I plan to refine the UI—mainly by adding multiple distortion options for cases where the default warp isn’t giving the expected results.

ChatGPT’s own code-generation capabilities (the Codex preview) helped me build the extension used for this experiment—which adds a fun layer of irony to the whole thing.

I’m currently available for Front-End or Full-Stack development roles, including freelance opportunities.
If you’re interested in working together, feel free to reach out—my email is ivanca at gmail.