# Hierarchical Cross Network for Person Re-identification

### Contact
Huan-Cheng Hsu

email: tonihs@gmail.com

## Before start
- Watch the [demo video](https://youtu.be/7TGpS1_psJ4)!
- Install and run [Person Re-ranking (CVPR 2017)](https://github.com/zhunzhong07/person-re-ranking)

Results can be reproduced as follows:

|Market-1501 |   Rank-1 | mAP|
| --------   | -----  | ----  |
|IDE_ResNet_50  + Euclidean + re-ranking | 81.44% | 70.39%|

|CUHK03 |  Labeled | Labeled|  detected | detected|
| -------| -----  | ----  |----  |----  |
|Method |  Rank-1 | mAP|  Rank-1 | mAP|
|IDE_ResNet_50  + XQDA + re-ranking     | 38.1% | 40.3%|34.7% | 37.4%|

## Training HCN
- Replace original network definition and solver files in `models/target_database/` to [CUHK03_labeled](https://github.com/huanhsu/HCN/tree/master/HCN/CUHK03_labeled), [CUHK03_detected](https://github.com/huanhsu/HCN/tree/master/HCN/CUHK03_detected)or [Market1501](https://github.com/huanhsu/HCN/tree/master/HCN/Market1501)
- Modify `-solver` to the path of target solver in `experiments/target_database/target_database.sh`
- Run training script
- Modify `model =` to the path of `HCN_test.prototxt` in `evaluation/target_database_extract_feature.m`
- Run feature extraction
- Run evaluation

Results can be reproduced as follows:

|Market-1501 |   Rank-1 | mAP|
| --------   | -----  | ----  |
|HCN  + Euclidean + re-ranking | 84.09% | 74.28%|

|CUHK03 |  Labeled | Labeled|  detected | detected|
| -------| -----  | ----  |----  |----  |
|Method |  Rank-1 | mAP|  Rank-1 | mAP|
|HCN + XQDA + re-ranking     | 43.4% | 46.0%|40.9% | 43.0%|

## Training HCN+ Combined data
- Download [CUHK01](https://docs.google.com/spreadsheet/viewform?formkey=dF9pZ1BFZkNiMG1oZUdtTjZPalR0MGc6MA)
- Modify or create a file with locations of training images, here is an [example](https://github.com/huanhsu/HCN/blob/master/HCN_Combined/train_03_1501_01_2489.txt) 
- Correct the [path](https://github.com/huanhsu/HCN/blob/master/HCN_Combined/HCN_Combined_train_val.prototxt#L19)
- Replace original network definition and solver files in `models/target_database` to [HCN_Combined](https://github.com/huanhsu/HCN/tree/master/HCN_Combined)
- Modify `-solver` to the path of target solver in `experiments/target_database/target_database.sh`
- Run training script
- Modify `model =` to the path of `HCN_test.prototxt` in `evaluation/target_database_extract_feature.m`
- Run feature extraction
- Run evaluation

Results can be reproduced as follows:

|Market-1501 |   Rank-1 | mAP|
| --------   | -----  | ----  |
|HCN + Euclidean + re-ranking | 82.63% | 72.66%|

|CUHK03 |  Labeled | Labeled|  detected | detected|
| -------| -----  | ----  |----  |----  |
|Method |  Rank-1 | mAP|  Rank-1 | mAP|
|HCN + XQDA + re-ranking     | 44.0% | 46.9%|43.7% | 45.3%|

## Reference
Hierarchical Cross Network for Person Re-identification https://arxiv.org/abs/1712.06820
