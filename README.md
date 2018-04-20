# tf-faster-rcnn
This repository is based on the python Caffe implementation of faster RCNN available [here](https://github.com/rbgirshick/py-faster-rcnn).

**Note**: Several minor modifications are made when reimplementing the framework, which give potential improvements. If you are seeking to reproduce the results in the original paper, please use the [official code](https://github.com/ShaoqingRen/faster_rcnn) or maybe the [semi-official code](https://github.com/rbgirshick/py-faster-rcnn). For details about the faster RCNN architecture please refer to the paper [Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks](http://arxiv.org/pdf/1506.01497.pdf).

### Detection Performance
The current code supports **VGG16**, **Resnet V1** and **Mobilenet V1** models. We mainly tested it on plain VGG16 and Resnet101 (thank you @philokey!) architecture. As the baseline, we report numbers using a single model on a single convolution layer, so no multi-scale, no multi-stage bounding box regression, no skip-connection, no extra input is used. The only data augmentation technique is left-right flipping during training following the original Faster RCNN. All models are released.

With VGG16 (``conv5_3``):
  - Train on VOC 2007 trainval and test on VOC 2007 test, **70.8**.
  - Train on VOC 2007+2012 trainval and test on VOC 2007 test ([R-FCN](https://github.com/daijifeng001/R-FCN) schedule), **75.7**.
  - Train on COCO 2014 [trainval35k](https://github.com/rbgirshick/py-faster-rcnn/tree/master/models) and test on [minival](https://github.com/rbgirshick/py-faster-rcnn/tree/master/models) (*Iterations*: 900k/1190k), **30.2**.

With Resnet101 (last ``conv4``):
  - Train on VOC 2007 trainval and test on VOC 2007 test, **75.7**.
  - Train on VOC 2007+2012 trainval and test on VOC 2007 test (R-FCN schedule), **79.8**.
  - Train on COCO 2014 trainval35k and test on minival (900k/1190k), **35.4**.

More Results:
  - Train Mobilenet (1.0, 224) on COCO 2014 trainval35k and test on minival (900k/1190k), **21.8**.
  - Train Resnet50 on COCO 2014 trainval35k and test on minival (900k/1190k), **32.4**.
  - Train Resnet152 on COCO 2014 trainval35k and test on minival (900k/1190k), **36.1**.

Approximate *baseline* [setup](https://github.com/endernewton/tf-faster-rcnn/blob/master/experiments/cfgs/res101-lg.yml) from [FPN](https://arxiv.org/abs/1612.03144) (this repository does not contain training code for FPN yet):
  - Train Resnet50 on COCO 2014 trainval35k and test on minival (900k/1190k), **34.2**.
  - Train Resnet101 on COCO 2014 trainval35k and test on minival (900k/1190k), **37.4**.
  - Train Resnet152 on COCO 2014 trainval35k and test on minival (900k/1190k), **38.2**.

