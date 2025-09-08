# Kidney Ultrasound Classification and Segmentation

This repository implements a pipeline for segmenting and classifying kidney ultrasound images into Normal, CKD, and AKI categories. It includes:
- U-Net segmentation.
- Single-input classification (non-segmented images).
- Dual-input classification (original + segmented).

## Setup
1. Clone the repo: `git clone https://github.com/NAlkhaldi/kidney-ultrasound-classification.git`
2. Install dependencies: `pip install -r requirements.txt`
3. Update `config.yaml` with your paths.
4. Place data in `data/` (images, csv).

## Running Experiments
- Segmentation: `python src/segmentation.py --config config.yaml`
- Single-Input: `python src/single_input_classification.py --config config.yaml`
- Dual-Input: `python src/dual_input_classification.py --config config.yaml`

## Results
Models saved in `outputs/`. Metrics in JSON/CSV.

## License
This project is licensed under the MIT License. During review, access is restricted to authorized reviewers.
