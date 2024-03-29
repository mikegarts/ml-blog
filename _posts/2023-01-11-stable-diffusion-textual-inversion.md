---
title: "Experiments with stable diffusion - textual inversion"
---

Textual inversion is a technique that allows one to train a new "word" (and get a new embedding for that word)
in the space of all possible embeddings our model knows.
As a user you can load this new embedding and refer it during the de-noising process. 

A better and more formal description can be found [here](https://huggingface.co/docs/diffusers/training/text_inversion)
A video explaining this topic is part of the stable diffusion [lecture series](https://www.youtube.com/watch?v=0_BBRNYInx8) by fast.ai. 

Here is an example of leaning a specific [watercolor houses drawing *style*](https://huggingface.co/sd-concepts-library/barbosa)]. 
The learned style then transferred to other objects:
![Textual inversion](https://github.com/mikegarts/ml-blog/raw/main/resources/textual_inv.png)

One has to be careful - if guidance is too high (that is, how much the de-noising should stick to the prompt) - 
even a cat can suddenly become a watercolor drawing of a house:
![img.png](https://github.com/mikegarts/ml-blog/raw/main/resources/cat_house.png)

Image to image (style transfer) works quite well too, but you have to lower the guidance a bit:
![img.png](https://github.com/mikegarts/ml-blog/raw/main/resources/img2img.png)
![img.png](https://github.com/mikegarts/ml-blog/raw/main/resources/img2img_2.png)

[Training an object](https://huggingface.co/sd-concepts-library/chukotka) (and not a style) yielded nice results 
![img.png](https://github.com/mikegarts/ml-blog/raw/main/resources/chuk.png)

But failed to locate the learned object correctly in the context of the scene given the prompt, for example

> Prompt: "photo of *object* driving a red car, yellow eyes, masterpiece, trending, beautiful, sharp focus, cute"
> 
![img.png](https://github.com/mikegarts/ml-blog/raw/main/resources/fail.png)

There is a huge collection of community created concepts [here](https://huggingface.co/sd-concepts-library). <br>
I found that the simplest way to train a new embedding is 
using [this google colab notebook](https://colab.research.google.com/github/huggingface/notebooks/blob/main/diffusers/sd_textual_inversion_training.ipynb)<br>

[And here](https://mikegarts.github.io/ml-blog/2023/01/30/stable-diffusion-dreambooth.html) is an
exploration of another technique to customize generative diffusion modes called Dreambooth.
