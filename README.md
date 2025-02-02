## CIPS-3D

This repository will contain the code of the paper, </br > 
[CIPS-3D: A 3D-Aware Generator of GANs Based on Conditionally-Independent Pixel Synthesis](https://arxiv.org/abs/2110.09788).

:heavy_check_mark: (2021-10-27) All the code files have been released. The configuration files (yaml files) for training will be released next. Now I have provided a GUI script and models to facilitate the experiment of network interpolation (see below). If you find any problems, please open an issue. Have fun with it. 
<img src=".github/web_demo.png" height="400" width="700">

:heavy_check_mark: (2021-10-25) Thank you for your kind attention. The github star has reached two hundred. I will open source the training code in the near future. 

:heavy_check_mark: (2021-10-20)  We are planning to publish the training code here in December. But if the github star reaches two hundred, I will advance the date. Stay tuned :clock10:.


## Demo videos

https://user-images.githubusercontent.com/26176709/137924071-26f700b1-46dc-4c1d-bb2d-189e6cc09116.mp4

https://user-images.githubusercontent.com/26176709/137924277-751c342b-87c0-4539-8ab9-96b795d257ab.mp4

https://user-images.githubusercontent.com/26176709/137924346-dd628c97-64e5-4cf7-9e34-ac6c42a98d3d.mp4

https://user-images.githubusercontent.com/26176709/137924529-c38fa07c-9673-42ab-8a27-8e510d4c65ca.mp4

https://user-images.githubusercontent.com/26176709/137924557-1aa23be9-d079-472e-8a9f-0e08f78fdce8.mp4

https://user-images.githubusercontent.com/26176709/137924581-f5dbf759-1c8c-4dc3-9b85-26f215f0fde0.mp4


## Mirror symmetry problem

<img src="./.github/mirror_symm.png" width="800">

The problem of mirror symmetry refers to the sudden change of the direction of the bangs near the yaw angle of pi/2. We propose to use an auxiliary discriminator to solve this problem (please see the paper).

Note that in the initial stage of training, the auxiliary discriminator must dominate the generator more than the main discriminator does. Otherwise, if the main discriminator dominates the generator, the mirror symmetry problem will still occur. In practice, progressive training is able to guarantee this. We have trained many times from scratch. Adding an auxiliary discriminator stably solves the mirror symmetry problem. If you find any problems with this idea, please open an issue. 

## Envs

```bash

git clone --recursive https://github.com/PeterouZh/CIPS-3D.git
cd CIPS-3D

# Create virtual environment
conda create -y --name cips3d python=3.6.7
conda activate cips3d

pip install torch==1.8.2+cu102 torchvision==0.9.2+cu102 -f https://download.pytorch.org/whl/lts/1.8/torch_lts.html

pip install --no-cache-dir tl2==0.0.3
pip install --no-cache-dir -r requirements.txt

pip install -e torch_fidelity_lib
pip install -e pytorch_ema_lib

```

## Model interpolation 

Download the pre-trained model [G_ema_ffhq.pth](https://github.com/PeterouZh/CIPS-3D/releases/download/v0.0.1/G_ema_ffhq.pth) 
and [G_ema_cartoon.pth](https://github.com/PeterouZh/CIPS-3D/releases/download/v0.0.1/G_ema_cartoon.pth), and put them in `datasets/pretrained`.

Execute this command:
```bash
streamlit run --server.port 8650 -- scripts/web_demo.py  \
  --outdir results/model_interpolation \
  --cfg_file configs/web_demo.yaml \
  --command model_interpolation

```
Then open the browser: `http://your_ip_address:8650`.

You can debug this script with this command:
```bash
python scripts/web_demo.py  \
  --outdir results/model_interpolation \
  --cfg_file configs/web_demo.yaml \
  --command model_interpolation \
  --debug True

```

## Prepare dataset

```bash

```

## Finetune INR Net

```bash

```

## Training from scratch

```bash

```


## Citation

If you find our work useful in your research, please cite:
```

@article{zhou2021CIPS3D,
  title = {{{CIPS}}-{{3D}}: A {{3D}}-{{Aware Generator}} of {{GANs Based}} on {{Conditionally}}-{{Independent Pixel Synthesis}}},
  shorttitle = {{{CIPS}}-{{3D}}},
  author = {Zhou, Peng and Xie, Lingxi and Ni, Bingbing and Tian, Qi},
  year = {2021},
  eprint = {2110.09788},
  eprinttype = {arxiv},
  primaryclass = {cs, eess},
  archiveprefix = {arXiv}
}

```

## Acknowledgments

- pi-GAN from [https://github.com/marcoamonteiro/pi-GAN](https://github.com/marcoamonteiro/pi-GAN)
- CIPS from [https://github.com/saic-mdal/CIPS](https://github.com/saic-mdal/CIPS)
- StyleGAN2 from [https://github.com/rosinality/stylegan2-pytorch](https://github.com/rosinality/stylegan2-pytorch)
- torch-fidelity from [https://github.com/toshas/torch-fidelity](https://github.com/toshas/torch-fidelity)
- StudioGAN from [https://github.com/POSTECH-CVLab/PyTorch-StudioGAN](https://github.com/POSTECH-CVLab/PyTorch-StudioGAN)
- DiffAug from [https://github.com/mit-han-lab/data-efficient-gans](https://github.com/mit-han-lab/data-efficient-gans)

