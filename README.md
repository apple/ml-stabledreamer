# StableDreamer: Taming Noisy Score Distillation Sampling for Text-to-3D ([arXiv](https://arxiv.org/abs/2312.02189))


<div align="center">
<img src="https://github.com/apple/ml-stabledreamer/assets/5269043/c7e4ae22-43ca-4e64-8fe1-47c5eac514e9" width="100%"/>
</div>


<p align="center">
<a href="https://scholar.google.com/citations?hl=en&user=O0yBqysAAAAJ"> Pengsheng Guo</a>,
<a href="https://scholar.google.com/citations?hl=en&user=IMn1m2sAAAAJ"> Hanxiang Hao</a>,
<a href="https://scholar.google.com/citations?hl=en&user=gc7htXwAAAAJ"> Adam Caccavale</a>,
<a href="https://scholar.google.com/citations?hl=en&user=iILS6kQAAAAJ"> Zhongzheng Ren</a>,
<a href="https://scholar.google.com/citations?hl=en&user=3kumBZQAAAAJ"> Edward Zhang</a>,
<a href="https://scholar.google.com/citations?hl=en&user=0FbnKXwAAAAJ"> Qi Shan</a>,
<a href="https://scholar.google.com/citations?hl=en&user=6ZDIdEAAAAAJ"> Aditya Sankar</a>,
<a href="https://scholar.google.com/citations?hl=en&user=3B2c31wAAAAJ"> Alex Schwing</a>,
<a href="https://scholar.google.com/citations?hl=en&user=PghQbXMAAAAJ"> Alex Colburn</a>,
<a href="https://scholar.google.com/citations?hl=en&user=kf07AjoAAAAJ"> Fangchang Ma</a>
<br> Apple 
</p>


## Summary
We present StableDreamer, a methodology incorporating three advancements to tame noisy score distillation sampling (SDS). It reduces multi-face geometries, generates fine details, and converges stably. Specifically, our contributions include:
1. Interpreting SDS as a **reparametrized supervised reconstruction** problem, leading to new visualization that motivates the use of an annealing schedule for noise levels.
2. A two-stage training framework that combines **image and latent diffusion** for enhanced geometry and color quality.
3. Integration of **3D Gaussians** for text-to-3D generation, with novel regularization techniques for improved quality and convergence, to further improve fidelity and details. 

<details>
  <summary>Expand Abstract</summary>
  
*In the realm of text-to-3D generation, utilizing 2D diffusion models through score distillation sampling (SDS) frequently leads to issues such as blurred appearances and multi-faced geometry, primarily due to the intrinsically noisy nature of the SDS loss. Our analysis identifies the core of these challenges as the interaction among noise levels in the 2D diffusion process, the architecture of the diffusion network, and the 3D model representation. To overcome these limitations, we present StableDreamer, a methodology incorporating three advances. First, inspired by InstructNeRF2NeRF, we formalize the equivalence of the SDS generative prior and a simple supervised L2 reconstruction loss. This finding provides a novel tool to debug SDS, which we use to show the impact of time-annealing noise levels on reducing multi-faced geometries. Second, our analysis shows that while image-space diffusion contributes to geometric precision, latent-space diffusion is crucial for vivid color rendition. Based on this observation, StableDreamer introduces a two-stage training strategy that effectively combines these aspects, resulting in high-fidelity 3D models. Third, we adopt an anisotropic 3D Gaussians representation, replacing Neural Radiance Fields (NeRFs), to enhance the overall quality, reduce memory usage during training, and accelerate rendering speeds, and better capture semi-transparent objects. StableDreamer reduces multi-face geometries, generates fine details, and converges stably.*
</details>


## Results
| | DreamFusion | ProlificDreamer | Gsgen | StableDreamer (Ours) |
| :---: | :---: | :---: | :---: | :---: |
| <sub> a zoomed out dslr photo of a baby bunny sitting on top of a stack of pancakes </sub> | <img src="viz/f2acb6fe-362c-4883-9cce-788176600c8d.gif"/> | <img src="viz/930d84eb-8df7-442b-9795-50c92c9cb60b.gif"/> | <img src="viz/9296934d-b34c-4398-9ccd-f5e7530ff30c.gif"/> | <img src="viz/9c2b91f8-4a59-4c92-b9f5-d6850552df54.gif"/> | 
| <sub> a zoomed out dslr photo of a rabbit cutting grass with a lawnmow </sub> | <img src="viz/a1452749-08c3-49b8-b2f9-297806be6a33.gif"/> | <img src="viz/0e83440f-aab7-4a6b-8f8c-f3fd9fd9e9fb.gif"/> | <img src="viz/0a23bfff-78c9-4609-b47c-9ccd8a357d60.gif"/> | <img src="viz/1455a722-dea9-4cff-8841-e1f6a9906ba1.gif"/> | 
| <sub> a wide angle dslr photo of a colorful rooster </sub> | <img src="viz/0ed491e5-0c8d-44ac-95fe-6b062c196210.gif"/> | <img src="viz/fcefea5b-2134-458e-92c4-50e149911755.gif"/> | <img src="viz/125f8c41-da35-438a-8a08-2475faa8a1a2.gif"/> | <img src="viz/77b8a13d-c71f-45ee-9754-00aad07b71bb.gif"/> | 
| <sub> a dslr photo of a blue jay standing on a large basket of rainbow macarons </sub> | <img src="viz/e2fe5b5f-39da-40e7-9599-5206da0dd217.gif"/> | <img src="viz/86a6d4b4-c6f6-4c2c-8c42-2452d60ef6fe.gif"/> | <img src="viz/c708b7f9-dc4f-413e-b4d6-d6767a693eac.gif"/> | <img src="viz/487d4562-9cd7-4812-b3b5-3d52b5f3c455.gif"/> | 
| <sub> a dslr photo of a tarantula, highly detailed </sub> | <img src="viz/be01c6cb-31c9-49f0-9249-82aed8661000.gif"/> | <img src="viz/6e8e3415-6eab-4be7-a490-a73300465592.gif"/> | <img src="viz/b891ddc6-a8b2-470a-bc3c-088a66f1264a.gif"/> | <img src="viz/1d71d074-c210-40ea-a30e-d382288ddc1d.gif"/> | 
| <sub> a zoomed out dslr photo of a corgi wearing a top hat </sub> | <img src="viz/5b66b8be-b541-45a1-bdee-272091fe0271.gif"/> | <img src="viz/964921b7-5a68-4df9-8bfe-c1a3f5891d2c.gif"/> | <img src="viz/85db9a44-55cf-4e74-b5c8-e0f88a8e4a8d.gif"/> | <img src="viz/53805cb3-9ad1-46d2-bef7-5ec922430230.gif"/> | 
| <sub> humoristic san goku body mixed with wild boar head running, amazing high tech fitness room digital illustration </sub> | <img src="viz/443856f8-f8c1-4756-81e1-0235a54bbaf7.gif"/> | <img src="viz/955acf82-e2c7-4ec7-a4af-7f22dc5a7faf.gif"/> | <img src="viz/4d0723de-ff6d-4cae-8915-32e431726898.gif"/> | <img src="viz/f88d0ab3-0310-42b9-bf1f-972474ef417d.gif"/> | 




## Related links

Check out recent related work of StableDreamer:

* [Threestudio: a unified framework for 3D content creation](https://github.com/threestudio-project/threestudio)
* [3D Gaussian Splatting for Real-Time Radiance Field Rendering](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/)
* [Instant Neural Graphics Primitives with a Multiresolution Hash Encoding](https://nvlabs.github.io/instant-ngp/)
* [DreamFusion: Text-to-3D using 2D Diffusion](https://dreamfusion3d.github.io)
* [Magic3D: High-Resolution Text-to-3D Content Creation](https://nv-tlabs.github.io/publication/2022_arxiv_magic3d/)
* [ProlificDreamer: High-Fidelity and Diverse Text-to-3D Generation with Variational Score Distillation](https://ml.cs.tsinghua.edu.cn/prolificdreamer/)
* [Gsgen: Text-to-3D using Gaussian Splatting](https://gsgen3d.github.io)

## Citation

```
@misc{guo2023stabledreamer,
      title={StableDreamer: Taming Noisy Score Distillation Sampling for Text-to-3D}, 
      author={Pengsheng Guo and Hans Hao and Adam Caccavale and Zhongzheng Ren and Edward Zhang and Qi Shan and Aditya Sankar and Alexander G. Schwing and Alex Colburn and Fangchang Ma},
      year={2023},
      eprint={2312.02189},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```
