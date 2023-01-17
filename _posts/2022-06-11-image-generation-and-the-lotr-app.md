---
title: "Fastai 2022: lesson four exercise and the Lord of the rings app"
---

[lotr app](https://huggingface.co/spaces/mikegarts/lotr): A cute app that combines language modeling, language summarization and image generation using the stable diffusion model.

Here's how the [kaggle notebook](https://www.kaggle.com/code/michaelgartsbein/lotrtrain) with the description of how language model was fine tuned and some boilerplate code to upload 
the trained model to the huggingface hub.
I used the distilgpt2 model as the base and follwed the [language_modeling](https://huggingface.co/docs/transformers/tasks/language_modeling) 
tutorial on huggingface with some slight changes that reflect the structure of the dataset.

The app itself is quite simple, one thing to [note](https://huggingface.co/spaces/mikegarts/lotr/blob/main/app.py#L84) 
is callback trick used to reconstruct the image from the latent state.
```
            latents = 1 / 0.18215 * latents
            res = pipe.vae.decode(latents).sample
            res = (res / 2 + 0.5).clamp(0, 1)
            res = res.cpu().permute(0, 2, 3, 1).detach().numpy()
            res = pipe.numpy_to_pil(res)[0]
```
This one is taken from [here](https://github.com/huggingface/diffusers/blob/08a6dc8a5840e0cc09e65e71e9647321ab9bb254/src/diffusers/pipelines/stable_diffusion/pipeline_stable_diffusion.py#L401).
Of course this might break but it would be easy to fix is something changes in this area.
