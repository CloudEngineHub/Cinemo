## Cinemo: Consistent and Controllable Image Animation with Motion Diffusion Models<br><sub>Official PyTorch Implementation</sub>


[![Arxiv](https://img.shields.io/badge/Arxiv-b31b1b.svg)](https://maxin-cn.github.io/cinemo_project/) 
[![Project Page](https://img.shields.io/badge/Project-Website-blue)](https://maxin-cn.github.io/cinemo_project/)


This repo contains pre-trained weights, and sampling code for our paper exploring image animation with motion diffusion models (Cinemo). You can find more visualizations on our [project page](https://maxin-cn.github.io/cinemo_project/).

> [**Cinemo: Consistent and Controllable Image Animation with Motion Diffusion Models**](https://maxin-cn.github.io/cinemo_project/)<br>
> [Xin Ma](https://maxin-cn.github.io/), [Yaohui Wang](https://wyhsirius.github.io/), [Gengyun Jia](https://scholar.google.com/citations?user=_04pkGgAAAAJ&hl=zh-CN), [Xinyuan Chen](https://scholar.google.com/citations?user=3fWSC8YAAAAJ), [Yuan-Fang Li](https://users.monash.edu/~yli/), [Cunjian Chen](https://cunjian.github.io/), [Yu Qiao](https://scholar.google.com.hk/citations?user=gFtI-8QAAAAJ&hl=zh-CN) 
> <br>Monash University, Shanghai Artificial Intelligence Laboratory<br>Nanjing University of Posts and Telecommunications

we propose a novel method called Cinemo, which can perform motion-controllable image animation with strong consistency and smoothness. To improve motion smoothness, Cinemo learns the distribution of motion residuals, rather than directly generating subsequent frames. Additionally, a structural similarity index-based method is proposed to control the motion intensity. Furthermore, we propose a noise refinement technique based on discrete cosine transformation to ensure temporal consistency. These three methods help Cinemo generate highly consistent, smooth, and motion-controlled image animation results. Compared to previous methods, Cinemo offers simpler and more precise user control and better generative performance.
 
<div align="center">
    <img src="visuals/pipeline.svg" width="650">
</div>

## News
- (🔥 New) Jun. 2, 2024. 💥 The inference code is released. The checkpoint can be found [here](https://huggingface.co/maxin-cn/Cinemo/tree/main).


## Setup

First, download and set up the repo:

```bash
git clone https://github.com/maxin-cn/Cinemo
cd Cinemo
```

We provide an [`environment.yml`](environment.yml) file that can be used to create a Conda environment. If you only want 
to run pre-trained models locally on CPU, you can remove the `cudatoolkit` and `pytorch-cuda` requirements from the file.

```bash
conda env create -f environment.yml
conda activate cinemo
```


## Animation 

You can sample from our **pre-trained Cinemo models** with [`animation.py`](pipelines/animation.py). Weights for our pre-trained Cinemo model can be found [here](https://huggingface.co/maxin-cn/Cinemo/tree/main).  The script has various arguments to adjust sampling steps, change the classifier-free guidance scale, etc:

```bash
bash pipelines/animation.sh
```

Than you will get the follwoing results,

<table class="center">
<tr>
  <td style="text-align:center;"><b>Input image</b></td>
  <td style="text-align:center;"><b>Output video</b></td>
  <td style="text-align:center;"><b>Input image</b></td>
  <td style="text-align:center;"><b>Output video</b></td>
</tr>
<tr>
  <td><image src="visuals/animations/people_walking/0.jpg" autoplay></td>
  <td><image src="visuals/animations/people_walking/people_walking.gif" autoplay></td>
  <td><image src="visuals/animations/sea_swell/0.jpg" autoplay></td>
  <td><image src="visuals/animations/sea_swell/sea_swell.gif" autoplay></td>
</tr>
</table>

<!-- 插入视频和图像排列在一行并添加标题 -->
<div style="display: flex; align-items: center; justify-content: center; flex-wrap: wrap; text-align: center;">

  <!-- 第一张图像 -->
  <div style="width: 23%; margin-right: 5px;">
    <h4 style="margin: 0;">Input image</h4>
    <img src="visuals/animations/people_walking/0.jpg" alt="第一张图像" style="width: 100%; margin: 5px 0;">
  </div>

  <!-- 第一个视频 -->
  <div style="width: 23%; margin-right: 5px;">
    <h4 style="margin: 0;">Output video</h4>
    <img src="visuals/animations/people_walking/people_walking.gif" alt="第一张图像" style="width: 100%; margin: 5px 0;">
    <!-- <video controls style="width: 100%; margin: 5px 0;">
      <source src="visuals/animations/people_walking/people_walking.gif" type="video/mp4">
    </video> -->
  </div>
  
  <!-- 第二张图像 -->
  <div style="width: 23%; margin-right: 5px;">
    <h4 style="margin: 0;">Input image</h4>
    <img src="visuals/animations/sea_swell/0.jpg" alt="第二张图像" style="width: 100%; margin: 5px 0;">

  </div>
  
  <!-- 第二个视频 -->
  <div style="width: 23%;">
    <h4 style="margin: 0;">Output video</h4>
    <img src="visuals/animations/sea_swell/sea_swell.gif" alt="第一张图像" style="width: 100%; margin: 5px 0;">
    <!-- <video controls style="width: 100%; margin: 5px 0;">
      <source src="https://huggingface.co/maxin-cn/Cinemo/resolve/main/visuals/animations/sea_swell/sea_swell.mp4?download=true" type="video/mp4">
    </video> -->
  </div>

  <!-- 分隔caption -->
  <div style="width: 100%; text-align: center; margin-top: 1px; margin-bottom: 1px;">
    <div style="display: flex; justify-content: space-between;">
      <div style="width: 50%;">
        <h5 style="margin: 0;">"People Walking"</h5>
      </div>
      <div style="width: 50%;">
        <h5 style="margin: 0;">"Sea Swell"</h5>
      </div>
    </div>
  </div>

</div>

<!-- 第二行 -->
<!-- 插入视频和图像排列在一行并添加标题 -->
<div style="display: flex; align-items: center; justify-content: center; flex-wrap: wrap; text-align: center;">

  <!-- 第一张图像 -->
  <div style="width: 23%; margin-right: 5px;">
    <img src="visuals/animations/girl_dancing_under_the_stars/0.jpg" alt="第一张图像" style="width: 100%; margin: 5px 0;">
  </div>

  <!-- 第一个视频 -->
  <div style="width: 23%; margin-right: 5px;">
    <img src="visuals/animations/girl_dancing_under_the_stars/girl_dancing_under_the_stars.gif" alt="第一张图像" style="width: 100%; margin: 5px 0;">
    <!-- <video controls style="width: 100%; margin: 5px 0;">
      <source src="https://huggingface.co/maxin-cn/Cinemo/resolve/main/visuals/animations/girl_dancing_under_the_stars/girl_dancing_under_the_stars.mp4?download=true" type="video/mp4">
    </video> -->
  </div>
  
  <!-- 第二张图像 -->
  <div style="width: 23%; margin-right: 5px;">
    <img src="visuals/animations/dragon_glowing_eyes/0.jpg" alt="第二张图像" style="width: 100%; margin: 5px 0;">

  </div>
  
  <!-- 第二个视频 -->
  <div style="width: 23%;">
    <img src="visuals/animations/dragon_glowing_eyes/dragon_glowing_eyes.gif" alt="第二张图像" style="width: 100%; margin: 5px 0;">
    <!-- <video controls style="width: 100%; margin: 5px 0;">
      <source src="https://huggingface.co/maxin-cn/Cinemo/resolve/main/visuals/animations/dragon_glowing_eyes/dragon_glowing_eyes.mp4?download=true" type="video/mp4">
    </video> -->
  </div>

  <!-- 分隔caption -->
  <div style="width: 100%; text-align: center; margin-top: 1px; margin-bottom: 1px;">
    <div style="display: flex; justify-content: space-between;">
      <div style="width: 50%;">
        <h5 style="margin: 0;">"Girl Dancing under the Stars"</h5>
      </div>
      <div style="width: 50%;">
        <h5 style="margin: 0;">"Dragon Glowing Eyes"</h5>
      </div>
    </div>
  </div>

</div>


## Other Applications

You can also utilize Cinemo to other applications, such as motion transfer and video editing:

```bash
bash pipelines/video_editing.sh
```

Than you will get the follwoing results,
<!-- 插入视频和图像排列在一行并添加标题 -->
<div style="display: flex; align-items: center; justify-content: center; flex-wrap: wrap; text-align: center;">

  <!-- 第一个视频 -->
  <div style="width: 23%; margin-right: 5px;">
    <img src="visuals/video_editing/origin/a_corgi_walking_in_the_park_at_sunrise_oil_painting_style.gif" alt="第一张图像" style="width: 100%;">
    <!-- <video controls style="width: 100%;">
      <source src="visuals/video_editing/origin/a_corgi_walking_in_the_park_at_sunrise_oil_painting_style.mp4" type="video/mp4">
    </video> -->
    <p>Input video</p>
  </div>
  
  <!-- 第一张图像 -->
  <div style="width: 23%; margin-right: 5px;">
    <img src="visuals/video_editing/origin/0.jpg" alt="第一张图像" style="width: 100%;">
    <p>First frame</p>
  </div>
  
  <!-- 第二张图像 -->
  <div style="width: 23%; margin-right: 5px;">
    <img src="visuals/video_editing/edit/0.jpg" alt="第二张图像" style="width: 100%;">
    <p>edited first frame</p>
  </div>
  
  <!-- 第二个视频 -->
  <div style="width: 23%;">
    <img src="visuals/video_editing/edit/editing_a_corgi_walking_in_the_park_at_sunrise_oil_painting_style.gif" alt="第二张图像" style="width: 100%;">
    <!-- <video controls style="width: 100%;">
      <source src="visuals/video_editing/edit/editing_a_corgi_walking_in_the_park_at_sunrise,_oil_painting_style.mp4" type="video/mp4">
    </video> -->
    <p>Output video</p>
  </div>

</div>





<!-- ## Citation
If you find this work useful for your research, please consider citing it.
```bibtex
@article{ma2024Cinemo,
  title={Cinemo: Latent Diffusion Transformer for Video Generation},
  author={Ma, Xin and Wang, Yaohui and Jia, Gengyun and Chen, Xinyuan and Liu, Ziwei and Li, Yuan-Fang and Chen, Cunjian and Qiao, Yu},
  journal={arXiv preprint arXiv:2401.03048},
  year={2024}
}
``` -->


## Acknowledgments
Cinemo has been greatly inspired by the following amazing works and teams: [LaVie](https://github.com/Vchitect/LaVie) and [SEINE](https://github.com/Vchitect/SEINE), we thank all the contributors for open-sourcing.


## License
The code and model weights are licensed under [LICENSE](LICENSE).
