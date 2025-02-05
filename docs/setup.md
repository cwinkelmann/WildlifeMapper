
```shell
ssh cwinkelmann@10.188.2.1
```

```shell

eval "$(/home/cwinkelmann/miniconda3/bin/conda shell.bash hook)"
```

```shell

conda activate WildlifeMapper
cd /home/cwinkelmann/work/WildlifeMapper/wildlifemapper
```


```shell
export PYTHONPATH=$PYTHONPATH:/home/cwinkelmann/work/WildlifeMapper/

## training
CUDA_VISIBLE_DEVICES=0,1 torchrun --nproc_per_node=2 wildlifemapper/train.py --coco_file_train /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/train/coco_crops/coco_format.json --coco_file_val /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/val/coco_crops/coco_format.json --coco_folder_train /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/train/crops_1024_numNone_overlap0 --coco_folder_val /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/val/crops_1024_numNone_overlap0 --trained_model /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/box_model --work_dir /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/box_model --output_dir /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/box_model --batch_size 3 --num_workers 8 --use_wandb True --num_epochs 5 --checkpoint /home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/checkpoint/sam_vit_l_0b3195.pth 


```

### Inference
```shell
CUDA_VISIBLE_DEVICES=0 python wildlifemapper/visualize_prediction.py --coco_path /mnt/mara/coco_1024_fixed --pretrain_model_path ./exp/box_model/best_checkpoint.pth  --num_workers 2


```


```shell
--device
cuda
--coco_file_train
/home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/train/coco_crops/coco_format.json
--coco_file_val
/home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/val/coco_crops/coco_format.json
--coco_folder_train
/home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/train/crops_1024_numNone_overlap0
--coco_folder_val
/home/cwinkelmann/work/WildlifeMapper/wildlifemapper/exp/data/2025_01_11/val/crops_1024_numNone_overlap0
--output_dir
./exp/box_model
--use_wandb
yes
--batch_size
3
--num_workers
0
--resume
./exp/box_model/checkpoint_epoch_80.pth
--num_epochs
25