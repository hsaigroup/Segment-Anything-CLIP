# Conect Segment-Anything with CLIP
We aim to classify the output masks of [segment-anything](https://github.com/facebookresearch/segment-anything) with the off-the-shelf [CLIP](https://github.com/openai/CLIP) models. The cropped image corresponding to each mask is sent to the CLIP model.
<img src="https://github.com/PengtaoJiang/SAM-CLIP/blob/main/imgs/pipeline.png" width="100%" height="50%">

## Todo
1. We plan connect segment-anything with [MaskCLIP](https://github.com/chongzhou96/MaskCLIP).  
2. We plan to finetune on the COCO and LVIS datasets.  


## Run Demo
Download the [sam_vit_h_4b8939.pth](https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth) model from the SAM repository and put it at ```./SAM-CLIP/```. Follow the instructions to install segment-anything and clip packages using the following command. 
```
cd SAM-CLIP; pip install -e .
pip install git+https://github.com/openai/CLIP.git
```
Then run the following script:
```
sh run.sh
```

## Example 
Input an example image and a point (250, 250) to the SAM model. The input image and output three masks as follows:
<center><img src="https://github.com/PengtaoJiang/SAM-CLIP/blob/main/imgs/ADE_val_00000001.jpg" width="50%" height="50%"></center>

The three masks and corresponding predicted category are as follows:
<center>
<img src="https://github.com/PengtaoJiang/SAM-CLIP/blob/main/outs/ADE_val_00000001/outs.png" width="100%" height="50%"> 
</center>
<center>
<img src="https://github.com/PengtaoJiang/SAM-CLIP/blob/main/outs/ADE_val_00000001/logits.png" width="100%" height="50%"> 
</center>

You can change the point location at L273-274 of ```scripts/amp_points.py```.
```
## input points 
input_points_list = [[250, 250]]
label_list = [1]
```
