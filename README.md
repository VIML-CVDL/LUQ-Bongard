# [AAAI 2024] Few-Shot Learning from Augmented Label-Uncertain Queries in Bongard-HOI
This is the repository for paper "Few-Shot Learning from Augmented Label-Uncertain Queries in Bongard-HOI" [AAAI2024] 

Project page Link: https://chelsielei.github.io/LUQ/

## Installation
Install pytorch
```
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
```

Install the necessary packages with requirements.txt
```
pip install -r requirements.txt
```
## Dataset
Data Preparation
===

1. Download the images from [HAKE](http://hake-mvig.cn/) dataset. You may follow the [official instruction](https://github.com/DirtyHarryLYL/HAKE/tree/master/Images#download-images-for-hake). For your convenience, you may download all the images required by Bongard-HOI [here](https://zenodo.org/record/7079175/files/bongard_hoi_images.tar?download=1). The images should be extracted to `./assets/data/hake/images` and the file structure looks like:
    ```plain
    data
    └── hake
        └── images
            ├── hake_images_20190730
            ├── hcvrd
            ├── hico_20160224_det
            │   └── images
            │       ├── test2015
            │       └── train2015
            ├── openimages
            │   └── images
            ├── pic
            │   └── image
            │       ├── train
            │       └── val
            └── vcoco
                ├── train2014
                └── val2014
    ```

2. Download the Bongard-HOI annotations from [here](https://zenodo.org/record/7079175/files/bongard_hoi_annotations.tar?download=1) and extract them to `./Bongard/cache`

3. Download the detected bounding boxes from [here](https://zenodo.org/record/7079175/files/hico_faster_rcnn_R_101_DC5_3x_objectness.pkl?download=1) and extract them to `./Bongard/cache`

4. Download the pretrained ResNet-50 from [here](https://zenodo.org/record/7079175/files/resnet.tar?download=1) and extract them to `./Bongard/cache`

5. Download the detected human bounding boxes by DEKR from [here](https://drive.google.com/file/d/1eQz95ilcC3xCZVRAxsqNA3WeQufOmxTw/view?usp=drive_link) and extract them to `./Bongard/cache/DEKR`

6. Download the generated background-blended queries from [here](https://drive.google.com/file/d/1P2ysdID_4jpazxOqBlTpp2AdsGKVE0NI/view?usp=drive_link) and extract them to `./Bongard/cache/ldm_selected_v4`
Also download the related annotation file from [here](https://drive.google.com/file/d/15z5kt5uZJdGyhGHyAsg8u0trh_z1_q-u/view?usp=drive_link) and put into `./Bongard/cache`




## Training
```bash
cd Bongard 
python train_my_metric_st_ldm.py --config-file "configs/my_metric_st_ldm.yaml" 
```

## Testing
```bash
cd Bongard 
python train_my_metric_st_ldm.py --config-file "configs/my_metric_st_ldm.yaml"  --test_only --test_model "<path to best_model.pth>"
```

## Model Zoo
We provide weights pre-trained on Bongard-HOI for potential downstream applications. 

|Model|SOSA|SOUA|UOSA|UOUA|Avg|Weights|
|:-|:-:|:-:|:-:|:-:|:-:|:-:|
|Ours|`68.14`| `70.94`| `68.45`| `67.43`|`68.74`|[weights](https://drive.google.com/file/d/10W1lksHoCpMQxADPkbhMMZpUilWRpKbe/view?usp=drive_link)|



## Citation

If you find our work useful for your research, please consider citing us:

```bibtex
@inproceedings{lei2024few,
  title={Few-Shot Learning from Augmented Label-Uncertain Queries in Bongard-HOI},
  author={Lei, Qinqian and Wang, Bo and Tan, Robby T},
  booktitle={Proceedings of the AAAI Conference on Artificial Intelligence},
  volume={38},
  number={4},
  pages={2974--2982},
  year={2024}
}
```

## Acknowledgement
We gratefully thank the authors from [Bongard-HOI](https://github.com/NVlabs/Bongard-HOI/tree/master) and [DSN](https://github.com/chrysts/dsn_fewshot) for open-sourcing their code.
