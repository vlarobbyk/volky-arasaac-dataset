# Volky ARASAAC Modified Pictogram Dataset

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

## Overview

This dataset contains **modified versions** of pictograms from the **ARASAAC** repository, along with YOLO-format annotations for object detection. It was created for training the computer vision module of the **Volky** robot, an edge-AI educational assistant for early childhood education (ages 6–8).

- **Total classes:** 180
- **Total images:** 899 (720 train, 179 validation)
- **Images per class:** 4–5 (original + rotations 0°, 90°, 180°, 270° and color variations)
- **Format:** YOLO v11 (`.txt` annotations, normalized coordinates)
- **Modifications:** Rotations, brightness/contrast adjustments, and color variations applied to pictograms

## Dataset Structure
dataset_volky/

├── images/ <br />
│ ├── train_limpio/ # 720 training images <br />
│ └── val/ # 179 validation images <br />
├── labels/ <br />
│ ├── train_limpio/ # 720 corresponding label files <br />
│ └── val/ # 179 corresponding label files <br />
├── classes_v2_mapping.json # Class ID to class name mapping (180 classes) <br />
└── data_nuevo.yaml # YOLO dataset configuration file


## Source and Attribution

The original pictograms were obtained from the **ARASAAC** repository:

> **Source:** [ARASAAC](https://globalsymbols.com/symbolsets/arasaac)  
> **Author:** Sergio Palao  
> **Owner:** Government of Aragon (Spain)  
> **License:** [Creative Commons BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)

### Modifications Applied

- Rotations: 0°, 90°, 180°, and 270°
- Color variations (hue/saturation/brightness adjustments)
- Filename prefix: `final_` (distinguishes modified versions from originals)

## Usage

### Requirements
- Python 3.8+
- Ultralytics YOLO v11
- Any YOLO-compatible framework

### Example (Python)

```python
from ultralytics import YOLO

# Load model
model = YOLO('yolo11s.pt')

# Train using the provided dataset config
model.train(data='data_nuevo.yaml', epochs=150, imgsz=960, batch=64)
```

## Dataset Configuration (data_nuevo.yaml)
train: images/train_limpio

val: images/val

nc: 180

names: ['abrigo', 'abuela', ...]  # Full list in classes_v2_mapping.json

## License
This dataset is distributed under the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)** license, consistent with the original ARASAAC license.

You are free to:

* **Share** - copy and redistribute the material in any medium or format
* **Adapt** - remix, transform, and build upon the material

Under the following terms:

* **Attribution** - You must give appropriate credit, provide a link to the license, and indicate if changes were made.
* **NonCommercial** - You may not use the material for commercial purposes.
* **ShareAlike** - If you remix, transform, or build upon the material, you must distribute your contributions under the same license.

## Acknowledgments
**Sergio Palao** created the original pictograms for the Government of Aragon (Spain). We thank [ARASAAC](https://arasaac.org/) for making these resources freely available under an open license. This dataset was annotated using [CVAT](https://www.cvat.ai/)  (Computer Vision Annotation Tool).

## Contact
For questions or issues, please open an issue in this repository or contact the corresponding author.

## Citation
If you use this dataset in your research, please cite:
