---
title: "Experiments with stable diffusion - Dreambooth"
---

After exploring the [textual inversion here](https://mikegarts.github.io/ml-blog/2023/01/11/stable-diffusion-textual-inversion.html), 
now it is a good time to examine another technique that allows us to extend the capabilities of a generative diffusion model.

First - what are the differences between the Textual Inversion and the Dreambooth techniques? <br>
![dreambooth](https://github.com/mikegarts/ml-blog/raw/main/resources/dreambooth/chatgpt-diff.png) <br>
Well that wasn't helpful at all! Seems like we are on our own here trying to understand the difference.

As a reminder, in textual inversion, we are adding a new token to the model's vocabulary (like a new word in a language) 
and learning its "location" in embedding space (one way to think about it, at least). 
Later we can use the new token in our prompts, and the de-noising process will guide the result 
closer towards something that incorporates the new token (closer in this context means that the 
"distance" between the encoded representation of the image and the encoded representation of the prompt gets smaller).

<br>

![dreambooth](https://github.com/mikegarts/ml-blog/raw/main/resources/dreambooth/dreambooth.png) <br>

The output of the textual inversion training is a relatively small file - the new embedding we learned. 
Its size, depending on the model used, is just a few thousands of bytes since it's merely the coordinates
of our freshly learned embedding in the embedding space.
It is possible to load many new embeddings into existing model and inference session 
(for example using [automatic1111 UI](https://github.com/AUTOMATIC1111/stable-diffusion-webui)).
Textual inversion yielded some very impressive results in the field of 
style transfer as one can examine [here](https://mikegarts.github.io/ml-blog/2023/01/11/stable-diffusion-textual-inversion.html). 

<br>

[Dreambooth by google research](https://dreambooth.github.io/), 
is another technique to extend the capabilities of generative diffusion models, but this time we are 
re-training the whole model instead of learning a new embedding.
It also means that the output of the process is a new model file (a few GBs) and thus
combining a number of new concepts during the inference can be somewhat more cumbersome.
On the other hand - the quality of the generated content becomes much more detailed, especially when dealing
with objects (or pets/human subjects). This probably happens because we also train the super resolution 
component (the part that resizes our small resolution generated image to a larger image).

<br>

![dreambooth](https://github.com/mikegarts/ml-blog/raw/main/resources/dreambooth/dreambooth2.png)

The model I trained with the description of the training and source images can be found 
at the [huggingface hub here](https://huggingface.co/mikegarts/chukotkadb). 

<p align="center">

<img src="https://github.com/mikegarts/ml-blog/raw/main/resources/dreambooth/chukotkadb.png" /> <br>

</p>

A few more examples of generations, this time with more elaborate prompt. <br>

![chukotkadb diving](https://github.com/mikegarts/ml-blog/raw/main/resources/dreambooth/chukotkadb-diving.png)

Example of generation with variety of angles, depths of field and light. <br>

![chukotkadb in space](https://github.com/mikegarts/ml-blog/raw/main/resources/dreambooth/chukotkadb-space.png)

One can then use text to image capability and to further enhance the result to be more artistic, or to 
improve the guidance (and make the result to adhere more to the prompt) <br>

![chukotkadb jedi](https://github.com/mikegarts/ml-blog/raw/main/resources/dreambooth/chukotkadb-jedi.png)

The simplest way I found to train your own version of stable diffusion model is
using this [hugging face space](https://huggingface.co/spaces/multimodalart/dreambooth-training).
