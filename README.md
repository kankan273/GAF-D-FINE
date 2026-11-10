GAF-D-FINE

Implementation associated with the manuscript:

Geometry-aware feature refinement and localization-quality estimation for rail surface defect detection

GAF-D-FINE is developed on top of D-FINE-B4 for rail surface defect detection. The method introduces three task-specific components for shallow-detail refinement, geometry-aware boundary calibration, and localization-quality estimation.

Method Overview

GAF-D-FINE contains three main modules:

CARI-P2: Cross-scale consistency-aware detail injection.
It uses deeper semantic information to filter shallow high-resolution P2 features before selected detail responses are injected into P3.

ERM-DC: Extreme-aspect-ratio boundary distribution calibration.
It derives scale and aspect-ratio cues from the current predicted box and independently calibrates the four boundary distributions.

IR-SG-LQE: Scale-shape-guided localization-quality estimation with explicit IoU supervision.
It combines scale-shape cues, boundary-distribution statistics, and an IoU-supervised quality branch to improve localization-quality estimation and prediction ranking.

Main Results

On the internal test set, GAF-D-FINE achieves:

Method

mAP@0.5:0.95

AP50

AP75

D-FINE-B4

0.532

0.890

0.603

GAF-D-FINE

0.557

0.908

0.662

Compared with D-FINE-B4, the improvements are +2.5, +1.8, and +5.9 percentage points for mAP@0.5:0.95, AP50, and AP75, respectively.

Datasets

The experiments use the following publicly available rail-surface defect datasets:

Rail Surface Defects.v1
https://universe.roboflow.com/dataset-aq7x0/rail-surface-defects-flrty

RSDDs
https://github.com/neu-rail-rsdds/rsdds

Rail Defect Detection v1
https://universe.roboflow.com/cdta/rail-defect-detection-ohqib/dataset/1

Rail Surface Defects.v1 and RSDDs are used to construct the main dataset. Rail Defect Detection v1 is used only for external cross-source evaluation and is not used for training, model selection, hyperparameter tuning, or threshold tuning.

The category definitions from the different sources are unified into a single class, defect, and the annotations are converted to COCO detection format.

Experimental Setting

The main GAF-D-FINE experiments use:

Input resolution: 640 × 640

Backbone: HGNetv2-B4

Training epochs: 60

Batch size: 2

Optimizer: AdamW

Initial learning rate: 1e-4

Weight decay: 1e-4

Learning-rate schedule: Cosine

Warm-up: 5 epochs

Minimum learning rate: 1e-5

Decoder layers: 8

Number of queries: 600

Post-processing: Top-K 600

Random seed: 42

Evaluation: COCO AP

Repository Structure

The exact directory structure follows the implementation in this repository. The main files related to GAF-D-FINE include the model definitions, training configuration, training scripts, and evaluation scripts.

The proposed modules can be identified by the names:

CARI-P2

ERM-DC

IR-SG-LQE

Installation

This project is implemented with PyTorch and is based on the D-FINE codebase.

Please install the dependencies required by this repository before training or evaluation.

If a requirements.txt file is provided, the dependencies can be installed with:

pip install -r requirements.txt

Training

Prepare the datasets in COCO detection format and update the corresponding dataset paths in the configuration files.

Then run the training script provided in this repository using the configuration for GAF-D-FINE.

Because the repository structure may differ across environments, please use the configuration and command format included in the uploaded source code.

Evaluation

The evaluation follows the COCO detection protocol and reports:

mAP@0.5:0.95

AP50

AP75

Precision

Recall

F1-score

For Precision, Recall, and F1-score, the confidence threshold is 0.5 and the IoU threshold is 0.5.

Data and Code Availability

The datasets used in this work are publicly available from the links above.

The processed annotations, fixed data split, and implementation associated with the manuscript are provided through this repository and/or can be obtained from the corresponding author upon reasonable request.

Acknowledgment

This implementation is based on the D-FINE framework. We thank the authors of D-FINE and the maintainers of the public rail-surface defect datasets used in this study.

Citation

If you use this work, please cite the corresponding paper after publication.

@article{gafdfine,
  title   = {GAF-D-FINE: a rail surface defect detection model with geometry-aware feature refinement and localization-quality estimation},
  author  = {Liu, Xiangju and Qi, Lin},
  year    = {2026}
}


