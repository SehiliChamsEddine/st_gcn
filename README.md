# Custom 17-Joint Skeleton Graph for Action Recognition

This repository provides code to construct a 17-joint human skeleton graph for pose-based action recognition, suitable for use with graph convolutional networks (e.g., ST-GCN). The custom skeleton is designed for datasets where the joints are defined as follows:

- 0: nose
- 1: left_eye
- 2: right_eye
- 3: left_ear
- 4: right_ear
- 5: left_shoulder
- 6: right_shoulder
- 7: left_elbow
- 8: right_elbow
- 9: left_wrist
- 10: right_wrist
- 11: left_hip
- 12: right_hip
- 13: left_knee
- 14: right_knee
- 15: left_ankle
- 16: right_ankle

The skeleton connectivity is defined by the following edges:

```python
neighbor_link = [
    (0, 1),   # nose <-> left_eye
    (0, 2),   # nose <-> right_eye
    (1, 3),   # left_eye <-> left_ear
    (2, 4),   # right_eye <-> right_ear
    (0, 5),   # nose <-> left_shoulder
    (0, 6),   # nose <-> right_shoulder
    (5, 6),   # left_shoulder <-> right_shoulder
    (5, 7),   # left_shoulder <-> left_elbow
    (7, 9),   # left_elbow <-> left_wrist
    (6, 8),   # right_shoulder <-> right_elbow
    (8, 10),  # right_elbow <-> right_wrist
    (5, 11),  # left_shoulder <-> left_hip
    (6, 12),  # right_shoulder <-> right_hip
    (11, 12), # left_hip <-> right_hip
    (11, 13), # left_hip <-> left_knee
    (13, 15), # left_knee <-> left_ankle
    (12, 14), # right_hip <-> right_knee
    (14, 16), # right_knee <-> right_ankle
]
```

## Usage

To use this skeleton configuration, instantiate the `Graph` class with the `custom17` layout:

```python
from graph import Graph

G = Graph(layout='custom17', strategy='spatial')
```

## Acknowledgments

This repository adapts code and concepts from the following work:

> Sijie Yan, Yuanjun Xiong, Dahua Lin. "Spatial Temporal Graph Convolutional Networks for Skeleton-Based Action Recognition." Proceedings of the AAAI Conference on Artificial Intelligence. 2018.  
> [Paper link](https://arxiv.org/abs/1801.07455)  
> [Original ST-GCN codebase](https://github.com/yysijie/st-gcn)

If you use this code or its variants, please cite the original ST-GCN paper:

```bibtex
@inproceedings{yan2018spatial,
  title={Spatial Temporal Graph Convolutional Networks for Skeleton-Based Action Recognition},
  author={Yan, Sijie and Xiong, Yuanjun and Lin, Dahua},
  booktitle={AAAI Conference on Artificial Intelligence},
  year={2018}
}
```
