### Environment

The code is developed and tested under the following environment

* Python 3.8
* PyTorch 2.3.1
* CUDA 12.2
* 2 RTX3090 GPUs

### Training configurations

|hyper-parameters | Human3.6M | HumanEva-I | MPI-INF-3DHP |
|:----------:|:----------:|:----------:|:----------:|
|Initial learning rate | 2e-4 |  1e-3 |  4e-4 | 
| Weight decay | 0.98 | 0.99 | 0.98 |
|Training epochs | 30 |  500|  100|
|Time per epoch| 3.5h | 3m | 3.5m|


### Dataset

Our code is compatible with the dataset setup introduced by [Martinez et al.](https://github.com/una-dinosauria/3d-pose-baseline) and [Pavllo et al.](https://github.com/facebookresearch/VideoPose3D). Please refer to [PoseFormer](https://github.com/zczcwh/PoseFormer) to set up the Human3.6M dataset  (./data directory).  [data](https://pan.baidu.com/s/1uuQ9tJ_ZzUKKrrSvWexg7A?pwd=1234). 

### Evaluating pre-trained models

We provide the pre-trained 81-frame model (CPN detected 2D pose as input) [here](https://pan.baidu.com/s/1iQeJqX8gq0kHpnFKOijatQ?pwd=1234). To evaluate it, put it into the `./checkpoint` directory and run:

```bash
python run_poseformer.py -k cpn_ft_h36m_dbb -f 81 -c checkpoint --evaluate cpn81f.bin
```
`-f` controls how many frames are used as input. After 5 runs, the 81-frame model achieves achieves 43.08 $\pm$ 0.08 mm (MPJPE). 


We also provide pre-trained 81-frame model (Ground truth 2D pose as input) [here](https://pan.baidu.com/s/1iQeJqX8gq0kHpnFKOijatQ?pwd=1234). To evaluate it, put it into the `./checkpoint` directory and run:

```bash
python run_poseformer.py -k gt -f 81 -c checkpoint --evaluate gt81f.bin
```
After 5 runs, the 81-frame model achieves 27.94 $\pm$ 0.05 mm (MPJPE). 


### Training new models

* To train a model from scratch (CPN detected 2D pose as input), run:

```bash
python run_poseformer.py -k cpn_ft_h36m_dbb -f 81 -lr 0.0002 -lrd 0.98
```


* To train a model from scratch (Ground truth 2D pose as input), run:

```bash
python run_poseformer.py -k gt -f 81 -lr 0.0002 -lrd 0.99
```


### Visualization and other functions

We keep our code consistent with [VideoPose3D](https://github.com/facebookresearch/VideoPose3D), [PoseFormer](https://github.com/zczcwh/PoseFormer). Please refer to their project page for further information. 


## Acknowledgement

Part of our code is borrowed from [VideoPose3D](https://github.com/facebookresearch/VideoPose3D), [PoseFormer](https://github.com/zczcwh/PoseFormer). We thank the authors for releasing the codes.
