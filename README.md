Mask Scoring R-CNN (MS R-CNN)
-----------------
This project is based on maskrcnn-benchmark https://github.com/facebookresearch/maskrcnn-benchmark

Network
-----------------
![alt text](demo/network.png)


Preparing
-----------------
  Preparing follows [MASKRCNN_README.md] (MASKRCNN_README.md)

Running
----------------

```
  Single GPU Training
  python tools/train_net.py --config-file "configs/e2e_ms_rcnn_R_50_FPN_1x.yaml" SOLVER.IMS_PER_BATCH 2 SOLVER.BASE_LR 0.0025 SOLVER.MAX_ITER 720000 SOLVER.STEPS "(480000, 640000)" TEST.IMS_PER_BATCH 1
  
  Multi-GPU Training
  export NGPUS=8
  python -m torch.distributed.launch --nproc_per_node=$NGPUS tools/train_net.py --config-file "configs/e2e_ms_rcnn_R_50_FPN_1x.yaml" 
```


   
Results
------------
| NetWork  | Method | mAP(mask) | mAP(det)  |
|----------|--------|-----------|-----------|
| ResNet-50 FPN | Mask R-CNN | 34.2 | 37.8 |
| ResNet-50 FPN | MS R-CNN | 35.6 | 37.9 |
| ResNet-101 FPN | Mask R-CNN | 36.1 | 40.1 |
| ResNet-101 FPN | MS R-CNN | 37.4 | 40.1 |

