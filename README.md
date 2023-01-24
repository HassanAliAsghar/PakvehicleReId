
## Installation
1. cd to your preferred directory and run ' https://github.com/HassanAliAsghar/PakvehicleReId '.
2. Install dependencies by pip install -r requirements.txt (if necessary).
## Datasets
+ [PakvehicleReID]()




## Models
+ resnet50
## Losses
+ cross entropy loss
+ triplet loss

## Tutorial
### train
Input arguments for the training scripts are unified in [args.py](./args.py).
To train an image-reid model, you can do
```
python train_xent_tri.py \
-s Pakvehiclereid \    #source dataset for training
-t Pakvehiclereid \    # target dataset for test
--height 128 \ # image height
--width 256 \ # image width
--optim amsgrad \ # optimizer
--lr 0.0003 \ # learning rate
--max-epoch 60 \ # maximum epoch to run
--stepsize 20 40 \ # stepsize for learning rate decay
--train-batch-size 64 \
--test-batch-size 100 \
-a resnet50 \ # network architecture
--save-dir log/resnet50-Pakvehiclereid \ # where to save the log and models
--gpu-devices 0 \ # gpu device index
```
### test
Use --evaluate to switch to the evaluation mode. In doing so, no model training is performed.

```
python test_imgreid.py \
-s Pakvehiclereid \ # this does not matter any more
-t Pakvehiclereid \ # you can add more datasets here for the test list
--height 128 \
--width 256 \
--test-size 800 \
--test-batch-size 100 \
--evaluate \
-a resnet50 \
--load-weights path_to_model.pth.tar \
--save-dir log/Pakvehiclereid \
--gpu-devices 0 \
```



