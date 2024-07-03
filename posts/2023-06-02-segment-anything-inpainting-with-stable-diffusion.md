---
title: Segment Anything Inpainting with Stable Diffusion
author: pejkster
---

Hello AI Art Weekly community 👋

[Nejc](https://www.linkedin.com/in/nejcsusec/) here. I love creating and I’ve
been diving deep into AI tools since July last year and have worked on a lot of
projects like an [interactive client
pitch](https://nejcsusec.beehiiv.com/p/interactive-client-pitching) or turning [concept artwork into final
products](https://nejcsusec.beehiiv.com/p/concept-final-product).

In this post we'll cover how to add details to generated images by extracting a
character from a source image with Meta's Segment Anything AI model and make use
of Stable Diffusion's inpainting to retain the style of the original image. For
this you'll need an image processing software like Photoshop and the
Automatic1111 WebUI.

> Tulpa's note: [RunDiffusion](https://app.rundiffusion.com?ref=dreaming60) is a
good and affordable cloud solution.

Inpainting is an incredible tool within Stable Diffusion – especially when
combined with ControlNET and has a lot of use cases. Putting characters and
objects into an image is just one of them. So let's dive in!

I start with the following image made in Midjourney:

![](https://fly.storage.tigris.dev/aiartweekly/assets/posts/segment-anything-inpainting-with-stable-diffusion/sam_01.webp)

The character is not how I want it to be. So I will composite a new character
into the image. So I created another character in Midjourney and used [SAM](https://segment-anything.com/demo#) to cut it out.
We upload our image and mark the areas of the character we want to cut out. Left click selects an area, right click deselects it.

![](https://fly.storage.tigris.dev/aiartweekly/assets/posts/segment-anything-inpainting-with-stable-diffusion/sam_02.webp)

When we’re happy with our selection, we can cut out the object and download it.

![](https://fly.storage.tigris.dev/aiartweekly/assets/posts/segment-anything-inpainting-with-stable-diffusion/sam_03.webp)

I then use Photoshop to composite the character into my image, but this works
with any modern image processing software.

![](https://fly.storage.tigris.dev/aiartweekly/assets/posts/segment-anything-inpainting-with-stable-diffusion/sam_04.webp)

The image looks pretty good already, but the character doesn’t fit naturally
into the scene. The lighting as well as the colors are off. The colors are also
not on brand with what the client is looking for. Fixing them can be done in
Photoshop by adjusting the hue. In this case, I adjusted the yellow colors to pink.

![](https://fly.storage.tigris.dev/aiartweekly/assets/posts/segment-anything-inpainting-with-stable-diffusion/sam_05.webp)

Now it’s time for AI to help.

I will put this image into Automatic1111's img2img inpaiting tab, mask
the knight in the image, and adjust my settings.

![](https://fly.storage.tigris.dev/aiartweekly/assets/posts/segment-anything-inpainting-with-stable-diffusion/sam_06.webp)

The most important settings are:

- Set `Masked content` to `original`
- Set `Inpaint area` to `Only masked` (which will only affect the masked area)
- Set `Denoising strength` to whatever you want – the higher the number the more
  the original image will be modified.

I also activate the ControlNet option with the `canny` model. This will create outlines from the original image to preserve the structure of our character.

With this setup, I write my prompt: `highly detailed 2d illustration of a knight holding a torch, in the style of
fantasy d&d with dark black and bright pink colors`, generate a new image, and voilà:

![](https://fly.storage.tigris.dev/aiartweekly/assets/posts/segment-anything-inpainting-with-stable-diffusion/sam_07.webp)

It might not look like much, but **details are what create a cohesive
storytelling experience**. Combining different AI or non AI tools together is
incredibly powerful and allows us to create in new ways we haven’t been able to create before.

I hope you’ve been enjoying this Segment Anything Inpainintg supported workflow
breakdown. Now it's your turn, keep creating and don't forget to have fun!
