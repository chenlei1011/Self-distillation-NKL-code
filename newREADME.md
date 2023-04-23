We use the backbone of F3Net as baseline and the student network, which is run in trainbaseline.py.
Our self-distillation code is run in trainour.py.
trainbaseline.py and trainour.py are in the floder "src".

## Download dataset

Download the following datasets and unzip them into `data` folder

- [PASCAL-S](http://cbi.gatech.edu/salobj/)
- [COD]( https://dengpingfan.github.io/pages/COD.html) 
- [HKU-IS](https://i.cs.hku.hk/~gbli/deep_saliency.html)
- [DUT-OMRON](http://saliencydetection.net/dut-omron/)
- [THUR]( https://mmcheng.net/code-data/)

The F3Net information is followed.

## [F3Net: Fusion, Feedback and Focus for Salient Object Detection](https://arxiv.org/pdf/1911.11445.pdf)
by Jun Wei, Shuhui Wang, Qingming Huang


## Prerequisites
- [Python 3.5](https://www.python.org/)
- [Pytorch 1.3](http://pytorch.org/)
- [OpenCV 4.0](https://opencv.org/)
- [Numpy 1.15](https://numpy.org/)
- [TensorboardX](https://github.com/lanpa/tensorboardX)
- [Apex](https://github.com/NVIDIA/apex)


## Clone repository

```shell
git clone git@github.com:weijun88/F3Net.git
cd F3Net/
```


## Download model

- If you want to test the performance of F3Net, please download the [model](https://drive.google.com/file/d/1jcsmxZHL6DGwDplLp93H4VeN2ZjqBsOF/view?usp=sharing) into `out` folder
- If you want to train your own model, please download the [pretrained model](https://download.pytorch.org/models/resnet50-19c8e357.pth) into `res` folder

## Training

```shell
    cd src/
    python3 train.py
```
- `ResNet-50` is used as the backbone of F3Net and `DUTS-TR` is used to train the model
- `batch=32`, `lr=0.05`, `momen=0.9`, `decay=5e-4`, `epoch=32`
- Warm-up and linear decay strategies are used to change the learning rate `lr`
- After training, the result models will be saved in `out` folder

## Testing

```shell
    cd src
    python3 test.py
```
- After testing, saliency maps of `PASCAL-S`, `ECSSD`, `HKU-IS`, `DUT-OMRON`, `DUTS-TE` will be saved in `eval/F3Net/` folder.

## Saliency maps & Trained model
- saliency maps: [Baidu](https://pan.baidu.com/s/1ZIfZ90FoqlrSdoD31Lul5g) [Google](https://drive.google.com/file/d/1FfZtzfSX6-hlwar4yJYLuGogGbLW9sYe/view?usp=sharing)
- trained model: [Baidu](https://pan.baidu.com/s/1qlqiCG0d9o2wH8ddeVJsSQ) [Google](https://drive.google.com/file/d/1jcsmxZHL6DGwDplLp93H4VeN2ZjqBsOF/view?usp=sharing)


## Evaluation
- To evaluate the performace of F3Net, please use MATLAB to run `main.m`
```shell
    cd eval
    matlab
    main
```
- Quantitative comparisons 
![performace](./fig/table.png)

- Qualitative comparisons 
![sample](./fig/case.png)

