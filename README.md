### State
The current state of the manuscript is under review. If the manuscript is accepted, we will release all the code and pre-trained models.

### Environment

The code is developed and tested under the following environment

* Python 3.8
* PyTorch 2.3.1
* CUDA 12.2

### Dataset

Our code is compatible with the dataset setup introduced by [Martinez et al.](https://github.com/una-dinosauria/3d-pose-baseline) and [Pavllo et al.](https://github.com/facebookresearch/VideoPose3D). Please refer to [PoseFormer](https://github.com/zczcwh/PoseFormer) to set up the Human3.6M dataset  (./data directory). 

### Evaluating pre-trained models

We provide the pre-trained 81-frame model (CPN detected 2D pose as input) [here](https://drive.google.com/file/d/1oX5H5QpVoFzyD-Qz9aaP3RDWDb1v1sIy/view?usp=sharing). To evaluate it, put it into the `./checkpoint` directory and run:

```bash
python run_poseformer.py -k cpn_ft_h36m_dbb -f 81 -c checkpoint --evaluate cpn81f.bin
```

We also provide pre-trained 81-frame model (Ground truth 2D pose as input) [here](https://drive.google.com/file/d/18wW4TdNYxF-zdt9oInmwQK9hEdRJnXzu/view?usp=sharing). To evaluate it, put it into the `./checkpoint` directory and run:

```bash
python run_poseformer.py -k gt -f 81 -c checkpoint --evaluate gt81f.bin
```


### Training new models

* To train a model from scratch (CPN detected 2D pose as input), run:

```bash
python run_poseformer.py -k cpn_ft_h36m_dbb -f 81 -lr 0.0002 -lrd 0.98
```

`-f` controls how many frames are used as input. 81 frames achieves achieves 43.0 mm. 

* To train a model from scratch (Ground truth 2D pose as input), run:

```bash
python run_poseformer.py -k gt -f 81 -lr 0.0002 -lrd 0.99
```

81 frames achieves 27.9 mm (MPJPE). 

### Visualization and other functions

We keep our code consistent with [VideoPose3D](https://github.com/facebookresearch/VideoPose3D), [PoseFormer](https://github.com/zczcwh/PoseFormer). Please refer to their project page for further information. 


## Acknowledgement

Part of our code is borrowed from [VideoPose3D](https://github.com/facebookresearch/VideoPose3D), [PoseFormer](https://github.com/zczcwh/PoseFormer). We thank the authors for releasing the codes.
