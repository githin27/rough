# rough
just created for understanding
<h1> <align="center"> Hi, I am Githin </h1>

<h2>Uformer: A General U-Shaped Transformer for Image Restoration (Reimplemented)</h2>


Paper link: [[Arxiv]](https://arxiv.org/abs/2106.03106) [[CVPR]](https://openaccess.thecvf.com/content/CVPR2022/papers/Wang_Uformer_A_General_U-Shaped_Transformer_for_Image_Restoration_CVPR_2022_paper.pdf)



<hr>
<i>
<p style="text-align: justify;">
The paper introduces Uformer, a powerful and efficient architecture based on Transformers. It is specifically designed for image restoration tasks. Uformer uses a hierarchical encoder-decoder network, employing Transformer blocks. Two key elements make Uformer suitable for this task. The first element is the use of a local-enhanced window Transformer block. This block employs non-overlapping window-based self-attention to reduce computational requirements. Additionally, it utilizes depth-wise convolution in the feed-forward network to better capture local context. The second key element is the implementation of three skip-connection schemes. These schemes effectively transfer information from the encoder to the decoder, enhancing the restoration process. By combining these two design elements, Uformer demonstrates a strong ability to capture important relationships for image restoration.</p></i>

![Uformer](fig/Uformer.png)

## Package dependencies
The project is built with PyTorch 1.9.0, Python3.7, CUDA11.1. For package dependencies, you can install them by:
```bash
pip install -r requirements.txt
```

## Pretrained model
- Uformer_B: [SIDD](https://mailustceducn-my.sharepoint.com/:u:/g/personal/zhendongwang_mail_ustc_edu_cn/Ea7hMP82A0xFlOKPlQnBJy0B9gVP-1MJL75mR4QKBMGc2w?e=iOz0zz) |
[GoPro](https://mailustceducn-my.sharepoint.com/:u:/g/personal/zhendongwang_mail_ustc_edu_cn/EfCPoTSEKJRAshoE6EAC_3YB7oNkbLUX6AUgWSCwoJe0oA?e=jai90x)

## Results from the pretrained model
- Uformer_B: [SIDD](https://mailustceducn-my.sharepoint.com/:f:/g/personal/zhendongwang_mail_ustc_edu_cn/EtcRYRDGWhBIlQa3EYBp4FYBao7ZZT2dPc5k1Qe-CdPh3A?e=PjBMub) |  [GoPro](https://mailustceducn-my.sharepoint.com/:f:/g/personal/zhendongwang_mail_ustc_edu_cn/ElFalK0Qb8NHnyvhkSe1APgB5D0urGRMLnu2nBXJhtzdIw?e=D2XBhS) 


## Data preparation 
### Denoising
For training data of SIDD, you can download the SIDD-Medium dataset from the [official url](https://www.eecs.yorku.ca/~kamel/sidd/dataset.php).
Then generate training patches for training by:
```python
python3 generate_patches_SIDD.py --src_dir ../SIDD_Medium_Srgb/Data --tar_dir ../datasets/denoising/sidd/train
```

For evaluation on SIDD and DND, you can download data from [here](https://mailustceducn-my.sharepoint.com/:f:/g/personal/zhendongwang_mail_ustc_edu_cn/Ev832uKaw2JJhwROKqiXGfMBttyFko_zrDVzfSbFFDoi4Q?e=S3p5hQ).


### Deblurring
For training and evaluation on GoPro,download data from [here](https://mailustceducn-my.sharepoint.com/:f:/g/personal/zhendongwang_mail_ustc_edu_cn/Ev832uKaw2JJhwROKqiXGfMBttyFko_zrDVzfSbFFDoi4Q?e=S3p5hQ).


Then put all the denoising data into `../datasets/denoising`, and all the deblurring data into `../datasets/deblurring`.

## Training
### Denoising
To train Uformer on SIDD, you can begin the training by:

```sh
sh script/train_denoise.sh
```
### Deblurring
To train Uformer on GoPro, you can begin the training by:

```sh
sh script/train_motiondeblur.sh
```


## Evaluation
To evaluate Uformer, you can run:

```sh
sh script/test.sh
```
For evaluate on each dataset, you should uncomment corresponding line.






