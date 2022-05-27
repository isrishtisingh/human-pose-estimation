# Human Pose Estimation


## Pose Estimation Demo using Mediapipe:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1wIY4GWsi2bkpQoFWd2iZrcDx5tJW-alr?usp=sharing)


## Pose estimation Demo Using HRNet:

![Example](https://github.com/isrishtisingh/human-pose-estimation/blob/2d8a2b33d0f60aba77174ef78088c1e64dd45325/output.gif)


## HRNet Summary

### What is HRNet
HRNet stands for High-Resolution Network, which refers to the high resolution of the images being processed. HRNet is a state-of-the-art algorithm in the field of semantic segmentation, facial landmark detection, and human pose estimation.
The network behind HRNet is called HRNetV1 and it “maintains high-resolution representations by connecting high-to-low resolution convolutions in parallel, where there are repeated multiscale fusions across parallel convolutions.”


### Need for HRNet
In traditional Encoder decoder type architectures(eg. UNet and SegNet) the HR information is projected down to a low resolution latest space which results in loss of spatial information. When the decoder decodes back the image from the latent representation, the high resolution info is lost. 

To improve this aspect, HRNet is introduced which instead of projecting the feature space sequentially to lower resolution, parallely computes all resolutions. In this way it preserves both the high resolution and lower resolution information of the inputs.


### Areas of Application:
- Semantic Segmentation
- Facial Landmark Detection
- Human Pose Estimation 


### HRNet Working Principle
In HRNet, rather than down sampling the input to lower resolutions and higher dimensional representation, HRNet preserves all the levels of resolutions and performs fusion at each stage among these different levels of representation.
In the first stage, the higher resolution feature map is retained using the same padding convolution. In the later stages, the lower level representation is generated using strided convolutions over the previous stage’s feature map and this is preserved in parallel with the high resolution features. At the boundary, there is a fusion of both levels of features using a multi resolution fusion block. The Higher resolution when fused with the low resolution feature map, transfers better spatial info learnt at the higher level representation and when the low level feature is merged with the high resolution feature map, better semantic information is transferred into the high resolution feature map. Hence making both the feature maps richer with information. The fusions from higher resolution to lower resolution are handled using 1x1 convs at suitable places and the upsampling fusion is handled using simple bilinear upsampling. The similar process is extended and 2 more levels of representations are generated and all are fused together to transfer the information learnt by each representation to each other. 
At the final layer, depending on the task, the output no of channels are decided(by either fusing all the levels in applications like semantic segmentation) or generating required no of channels in the output(for applications like pose estimation or facial keypoint detection)


### Parameter Analysis
Initial speculations were that the HRNet should have a large no of parameters because of the multiple feature level parallel architecture but the authors in the paper have presented a detailed ablation on the no of parameters and the GFLOPS of operations performed for different tasks on different datasets. In summary, the HRNet-w32 is comparable to a resnet 50 network in no of parameters and the HRNet-w48 is comparable to a resnet 152 in size. The number of parameters are lesser than the resnet equivalents and the GFLOPS are drastically less compared to the resner counterparts yet the performance are significantly better than the resner counterparts.


### Conclusion
HRNet and its variants (HRNetV1, HRNetV2, HRNetV2p) are state-of-the-art for many machine learning disciplines in the field of computer vision. 


### References:
- https://arxiv.org/pdf/1902.09212.pdf
- https://2d3d.ai/index.php/2020/06/14/human-pose-estimation-hrnet/
- https://www.youtube.com/watch?v=aeHm6NDXMBc&ab_channel=2d3d.ai

### Code References:
- https://github.com/stefanopini/simple-HRNet
- https://github.com/leoxiaobin/deep-high-resolution-net.pytorch


