# Installation setup

### With conda
```bash
conda create -n swin_seg python=3.8 -y
source /trinity/shared/opt/anaconda3/bin/activate swin_seg
```

### With mamba
```bash
mamba create -n swin_seg python=3.8 -y
source /trinity/shared/opt/mambaforge3/bin/activate swin_seg
```

### Next steps
From repo root
```bash
pip3 install torch==1.7.1+cu110 torchvision==0.8.2+cu110 -f https://download.pytorch.org/whl/torch_stable.html
pip3 install -U openmim
mim install mmcv-full==1.3.0
pip3 install -e .
pip3 install yapf==0.40.1
```

# Train

## From scratch
```bash
bash tools/dist_train.sh configs/swin/upernet_swin_small_patch4_window7_512x512_160k_ade20k.py 1
```

## Finetune
TODO


# Test

## With test augs (higher scores)
```bash
python tools/test.py configs/swin/upernet_swin_small_patch4_window7_512x512_160k_ade20k.py /gpfs/gpfs0/dermilov_group/checkpoints/swin_seg/upernet_swin_small_patch4_window7_512x512.pth --eval mIoU --aug-test
```

## Without test augs (lower scores)
```bash
python tools/test.py configs/swin/upernet_swin_small_patch4_window7_512x512_160k_ade20k.py /gpfs/gpfs0/dermilov_group/checkpoints/swin_seg/upernet_swin_small_patch4_window7_512x512.pth --eval mIoU
```

