## Global-Part Collaborative Prompt Learning for Lifelong Person Re-Identification
### Installation

```
conda create -n clipreid python=3.8
conda activate clipreid
conda install pytorch==1.8.0 torchvision==0.9.0 torchaudio==0.8.0 cudatoolkit=10.2 -c pytorch
pip install yacs
pip install timm
pip install scikit-image
pip install tqdm
pip install ftfy
pip install regex
```

### Training

if you want to run lifelong ReID training for Order 1, you need to modify the bottom of configs/person/vit_clipreid.yml to

```
DATASETS:
    NAMES: ('market1501')
    ROOT_DIR: ('your_dataset_dir')
OUTPUT_DIR: 'your_output_dir'

    NAMES: ('dukemtmc')
    ROOT_DIR: ('your_dataset_dir')
OUTPUT_DIR: 'your_output_dir'

    NAMES: ('cuhk_sysu')
    ROOT_DIR: ('your_dataset_dir')
OUTPUT_DIR: 'your_output_dir'

     NAMES: ('msmt17')
    ROOT_DIR: ('your_dataset_dir')
OUTPUT_DIR: 'your_output_dir'
```

then run 

```
CUDA_VISIBLE_DEVICES=0 python train.py --config_file configs/person/vit.yml
```

### Evaluation

For example, if you want to test ViT-based CLIP-ReID for MSMT17

```
CUDA_VISIBLE_DEVICES=0 python test.py --config_file configs/person/vit.yml TEST.WEIGHT 'your_trained_checkpoints_path/ViT-B-16_60.pth'
```

### Acknowledgement

Codebase from [CLIP-ReID](https://github.com/Syliz517/CLIP-ReID), [TransReID](https://github.com/damo-cv/TransReID), [CLIP](https://github.com/openai/CLIP), and [CoOp](https://github.com/KaiyangZhou/CoOp).
