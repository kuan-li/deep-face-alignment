## Robust 2D and 3D Face Alignment Implemented in MXNet

This repository contains heatmap based approaches like stacked Hourglass and stacked U-Nets for robust 2D and 3D face alignment. Some popular blocks like bottleneck residual block, inception residual block, parallel and multi-scale (HPM) residual block and channel aggregation block (CAB) are also provided for building the structure of deep face alignment networks. All the codes in this repo are implemented in Python and MXNet.

The models for 2D face alignment are verified on IBUG, COFW and 300W test datasets by the normalised mean error (NME) respectively. For 3D face alignment, the 3D models are compared on AFLW2000-3D with the most recent state-of-the-art methods.

The training/validation dataset and testset are in below table:

| Data | Download Link | Description |
|:-:|:-:|:-:|
| train_testset2d.zip | [BaiduCloud](https://pan.baidu.com/s/1EbSx_j_GoNJqLwZyuclBAQ) or [GoogleDrive](https://drive.google.com/open?id=1XyZ5yFm-MGNlUiGG0dYRHRTdRiS33zPb), 490M | 2D training/validation dataset and IBUG, COFW, 300W testset |
| train_testset3d.zip | [BaiduCloud](https://pan.baidu.com/s/1idA68ga8ey-R9TGSwWO62A) or [GoogleDrive](https://drive.google.com/open?id=1i-gUFJhtiZP3uCmNbhLCzd4C4fb-Ljhk), 1.54G | 3D training/validation dataset and AFLW2000-3D testset |


The performances of 2D face alignment models are shown below. Accuracy is reported as the Normalised Mean Error (NME). To facilitate comparison with other methods on these datasets, we give mean error normalised by the diagonal of the ground truth bounding box and the eye centre distance. Each training model is denoted by Topology^StackBlock (d = DownSampling Steps) - BlockType - OtherParameters.

| Model | Model Size | IBUG  | COFW  | 300W  | Download Link |
|:-:|:-:|:-:| :-: | :-: | :-: |
| *Hourglass2(d=4)-Resnet* | 26MB | 2.051/7.819 | 2.276/7.094 | 1.891/6.640 | [BaiduCloud](https://pan.baidu.com/s/1xGXiykKrRyGKPXMXDRsMZw) or [GoogleDrive](https://drive.google.com/open?id=1YPfF3t4J33Zj5goIZBk15TsxbqHB90rR) |
| *Hourglass2(d=3)-HPM* | 38MB | 1.970/7.499 | 2.116/6.587 | 1.785/6.256 | [BaiduCloud](https://pan.baidu.com/s/1qOD-qthPqScsX913EMwKag) or [GoogleDrive](https://drive.google.com/open?id=1-rDuuzxw9civqz9wTtklYqT6k3utr6Gc) |
| *Hourglass2(d=4)-CAB* | 46MB |  1.912/7.289  |  1.992/6.216 |  1.658/5.816 | [BaiduCloud](https://pan.baidu.com/s/1sSfnxf9_myl7NS7QEddOfQ) or [GoogleDrive](https://drive.google.com/open?id=1o--WwpHoRw2W5bScan6t16vEKS53WBBm) |
| *Hourglass2(d=3)-CAB* | 37MB | **1.874/7.140** | **1.926/6.006** |**1.640/5.748** | [BaiduCloud](https://pan.baidu.com/s/1BysgX7X2p1g8X8nS01gFlA) or [GoogleDrive](https://drive.google.com/open?id=1AbTGhIBzUUINTH2GNL05tSWvOHnclRr4) |
| *SAT2(d=3)-CAB* | 40MB | 1.875/7.154 | 1.939/6.047 | 1.640/5.751 | [BaiduCloud](https://pan.baidu.com/s/1YQKaUwpBq1IWz8vawj6HWA) or [GoogleDrive](https://drive.google.com/open?id=1n-Nd4rdik-IWqIzgIEdssDKvZ7SwuOff) |


The performances of 3D face alignment models are shown below. Accuracy is reported as the Normalised Mean Error (NME). The mean error is normalised by the square root of the ground truth bounding box size.

| Model | Model Size | AFLW2000-3D  | Download Link |
| :-: | :-: | :-: | :-: |
| *SAT2(d=3)-CAB-3D* | 40MB |  **3.360**  | [BaiduCloud](https://pan.baidu.com/s/1kFO-kTk-ozZ2m494xoNbqw) or [GoogleDrive](https://drive.google.com/open?id=1lxHbWZa_l457oFX4tgSpFaubDKU7LNuq) |


Note: More pretrained models will be added soon.

## Environment

This repository has been tested under the following environment:

-   Python 2.7 
-   Ubuntu 18.04
-   Mxnet-cu90 (==1.3.0)

## Training

1.  Prepare the environment.

2.  Clone the repository.

3.  Download the training/validation dataset and unzip it to your project directory.
    
3.  You can define different loss-type/network structure/dataset in ``config.py``(from ``sample_config.py``).
    
4.  You can use ``CUDA_VISIBLE_DEVICES='0' train.py --network sdu`` to train SDU-net or ``CUDA_VISIBLE_DEVICES='0' train.py --network hourglass`` to train stacked hourglass network. Instead, you can also edit  _`train.sh`_  and run  _`sh ./train.sh`_  to train your models.

## Testing

  -  Download the pre-trained model and place it in *`./models/`*.

  -  You can use `python test.py` to test this alignment method.
  
## Results

![2D Alignment Results](https://raw.githubusercontent.com/deepinx/sdu-face-alignment/master/sample-images/landmark_test.png)

## License

MIT LICENSE


## Reference

```
@article{guo2018stacked,
  title={Stacked Dense U-Nets with Dual Transformers for Robust Face Alignment},
  author={Guo, Jia and Deng, Jiankang and Xue, Niannan and Zafeiriou, Stefanos},
  journal={arXiv preprint arXiv:1812.01936},
  year={2018}
}
```

## Acknowledgment

The code is adapted based on an intial fork from the [insightface](https://github.com/deepinsight/insightface) repository.

