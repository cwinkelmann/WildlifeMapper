<img src="./docs/thumbnail_wildlifemapper2.png" width="200">

## WildlifeMapper: Aerial Image Analysis for Multi-Species Detection and Identification

WildlifeMapper (WM) is a state-of-the-art model for detecting, locating, and identifying multiple animal species in aerial imagery. It introduces novel modules to enhance localization and identification accuracy, with a verified dataset of 11k images and 28k annotations. This repository contains code for WildlifeMapper, scripts to download and tool to visualize dataset ([**BisQue**](https://bisque2.ece.ucsb.edu/client_service/view?resource=https://bisque2.ece.ucsb.edu/data_service/00-TGbt6MLRm7VCn4mWmVaQsc)).

### [**WildlifeMapper: Aerial Image Analysis for Multi-Species Detection and Identification**](https://openaccess.thecvf.com/content/CVPR2024/papers/Kumar_WildlifeMapper_Aerial_Image_Analysis_for_Multi-Species_Detection_and_Identification_CVPR_2024_paper.pdf)
[Satish Kumar*](https://www.linkedin.com/in/satish-kumar-81912540/), [Bowen Zhang](), .. , [Jared A. Stabach](https://jaredstabach.com/), [Lacey Hughey](), .. , [B S Manjunath](https://vision.ece.ucsb.edu/people/bs-manjunath).

Official repository of our [**CVPR 2024**](https://openaccess.thecvf.com/content/CVPR2024/papers/Kumar_WildlifeMapper_Aerial_Image_Analysis_for_Multi-Species_Detection_and_Identification_CVPR_2024_paper.pdf) paper.

<img src="./docs/wildlifemapper_github.jpg" width="800">

This repository includes:
* Source code of WildlifeMapper.
* Pre-trained weights for the bounding box detector.
* Scripts to download Mara-Wildlife dataset (Approvals under review)
* Online tool to visualize Mara-Wildlife dataset ([**BisQue**](https://bisque2.ece.ucsb.edu/client_service/view?resource=https://bisque2.ece.ucsb.edu/data_service/00-TGbt6MLRm7VCn4mWmVaQsc))
* Code for custom data preparation for training/testing


![supported versions](https://img.shields.io/badge/python-(3.8--3.10)-brightgreen/?style=flat&logo=python&color=green)
![Library](https://img.shields.io/badge/Library-Pytorch-blue)
![GitHub license](https://img.shields.io/cocoapods/l/AFNetworking)


The repository follows the structure of paper, making it easy to follow and use/extend the work. If this research is helpful to you, please consider citing our paper (bibtex below)

## Citing
If this research is helpful to you, please consider citing our paper:

```
@inproceedings{kumar2024wildlifemapper,
  title={WildlifeMapper: Aerial Image Analysis for Multi-Species Detection and Identification},
  author={Kumar, Satish and Zhang, Bowen and Gudavalli, Chandrakanth and Levenson, Connor and Hughey, Lacey and Stabach, Jared A and Amoke, Irene and Ojwang, Gordon and Mukeka, Joseph and Mwiu, Stephen and others},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={12594--12604},
  year={2024}
}
```

## Usage

### Requirements
- Linux or macOS with Python >= 3.7
- Pytorch >= 1.7.0
- CUDA >= 10.0
- cudNN (compatible with CUDA)

### Installation
1. Clone the repository
2. Install dependencies
```
pip install -r requirements.txt
```

### Download the model
Please download the following model before running using the command below at the current location

```shell
wget https://dl.fbaipublicfiles.com/segment_anything/sam_vit_l_0b3195.pth wildlifemapper/exp/checkpoint/
```

###  Training Data Preparation
create 1024px image patches from the original images and annotations
```shell
TODO this code does not exist so far
```

### Training
```shell
CUDA_VISIBLE_DEVICES=0 python train.py --coco_path /Users/christian/data/training_data/2024_12_16/train/crops_1024_numNone_overlap0/coco/coco_format.json --output_dir ./exp/box_model --batch_size 1 --num_workers 0 --resume ./exp/box_model/checkpoint_epoch_240.pth
# run.sh
```


### Inference
```shell

```


## Dataset

See [here](https://bisque2.ece.ucsb.edu/client_service/view?resource=https://bisque2.ece.ucsb.edu/data_service/00-TGbt6MLRm7VCn4mWmVaQsc) for an overview of the dataset. The sample dataset can be downloaded [here](https://bisque2.ece.ucsb.edu/client_service/view?resource=https://bisque2.ece.ucsb.edu/data_service/00-TGbt6MLRm7VCn4mWmVaQsc).

We save masks per image as a json file. It can be loaded as a dictionary in python in the below format.

```python
{
    "image"                 : image_info,
    "annotations"           : [annotation],
}

image_info {
    "image_id"              : int,              # Image id
    "width"                 : int,              # Image width
    "height"                : int,              # Image height
    "file_name"             : str,              # Image filename
}

annotation {
    "id"                    : int,              # Annotation id
    "bbox"                  : [x, y, w, h],     # The box around the mask, in XYWH format
    "predicted_iou"         : float,            # The model's own prediction of the mask's quality
    "stability_score"       : float,            # A measure of the mask's quality
}
```

### [**Dataset visualization guide**]()
<img src="./docs/WildLifeMapper_data_visualization.gif" width="700">

## License
WildlifeMapper is released under the UCSB license. Please see the [LICENSE](./LICENSE) file for more information.

## Contributors

The WildlifeMapper project was made possible with the help of many contributors for all over the world: Satish Kumar, Bowen Zhang, Chandrakanth Gudavalli, Connor Levenson, Lacey Hughey, Jared A. Stabach, Irene Amoke, Gordon Ojwang’, Joseph Mukeka, Stephen Mwiu, Joseph Ogutu, Howard Frederick, B.S. Manjunath
