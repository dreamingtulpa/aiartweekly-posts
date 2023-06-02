---
title: Segment Anything Inpainting with Stable Diffusion
author: pejkster
---

Hello AI Art Weekly community 👋

[Nejc](https://www.linkedin.com/in/nejcsusec/) here. I love creating and I’ve
been diving deep into AI tools since July last year and have worked on a lot of
projects like an [interactive client
pitch](https://nejcsusec.beehiiv.com/p/interactive-client-pitching) or turning [concept artwork into final
products](https://nejcsusec.beehiiv.com/p/concept-final-product). and I want to show you how I use Stable Diffusion Inpainting to composite characters into images.

In this post we'll cover how to add details to generated images by extracting a
character from a source image with Meta's Segment Anything AI model and make use
of Stable Diffusion's inpainting to retain the style of the original image. For
this you'll need an image processing software like Photoshop and the
Automatic1111 WebUI.

> Tulpa's note: [RunDiffusion](https://app.rundiffusion.com?ref=dreaming60) is a
good and affordable cloud solution.

Inpainting is an incredible tool within Stable Diffusion. Especially when
combined with ControlNET. I use it for many use cases. Putting characters and
objects into an image is just one of them. So let's dive in. I start with this image made in
Midjourney:

![](tmp/assets/posts/sam_01.jpg)

The character is not how I want it to be. So I will composite a new character on
the image. I created the character in Midjourney and used [SAM](https://segment-anything.com/demo#) to cut it out.
We upload our image and mark the areas we want to cut out. Left click selects an area, right click deselects it.

![](tmp/assets/posts/sam_02.jpg)

When we’re happy with our selection, we can cut out the object and save/copy it.

![](tmp/assets/posts/sam_03.jpg)

I then use Photoshop to composite the character into my image.

![](tmp/assets/posts/sam_04.jpg)

The image might look pretty good already, but the character doesn’t fit naturally in the scene. The lighting as well as the colors are off. The colors are also not on brand with the client. Fixing the brand colors can be done in photoshop, by adjusting the hue. In my case I adjust the yellow colors to pink.

![](tmp/assets/posts/sam_05.jpg)

Now it’s time for AI to help.

I will put this image into Automatic1111's img2img inpaiting tab, mask
the knight in the image and adjust my settings as follows:

![](tmp/assets/posts/sam_06.jpg)

The most important ones are setting

- `Masked content` to `original`
- `Inpaint area` to `Only masked` (which will only affect the masked area)
- `Denoising strength` to whatever you want – the higher the number the more the original image will be modified

I put the same image in ControlNET with the `canny` model. This will create outlines from the original image to preserve the structure of our character.

With this setup I write my prompt: `highly detailed 2d illustration of a knight holding a torch, in the style of
fantasy d&d with dark black and bright pink colors` and generate a new image.

![](tmp/assets/posts/sam_07.jpg)

It might not look like much, but details are what create a cohesive storytelling experience. Combining different tools together, AI or non AI, is incredibly powerful. It allows us to create in ways we haven’t been able to create ever before. I hope you’ve been enjoying this AI supported workflow breakdown. Keep creating and don't forget to have fun!
