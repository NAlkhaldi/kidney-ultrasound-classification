# Kidney Ultrasound Classification and Segmentation

This repository implements a pipeline for segmenting and classifying kidney ultrasound images into Normal, Chronic Kidney Disease (CKD), and Acute Kidney Injury (AKI) categories. It includes:

- U-Net segmentation (teacher and student models for mask generation and kidney segmentation).
- Single-input classification (non-segmented images).
- Dual-input classification (original + segmented images).

## Setup

1. **Download the Repository**:
   - Visit [https://github.com/NAlkhaldi/kidney-ultrasound-classification](https://github.com/NAlkhaldi/kidney-ultrasound-classification), click **Code > Download ZIP**, and extract to a local folder.
   - Alternatively, use [GitHub Desktop](https://desktop.github.com): Clone the repository via **File > Clone repository**.

2. **Install Dependencies**:
   - Download `requirements.txt` from the repository.
   - **In Google Colab**:
     - Upload `requirements.txt` to Google Drive (e.g., `/content/drive/MyDrive/Datasets/Projec_Unetbased/`).
     - Run in a Colab cell:
       ```
       !pip install -r /content/drive/MyDrive/Datasets/Projec_Unetbased/requirements.txt
       ```
   - **Locally (using VS Code or PyCharm)**:
     - Open the project folder in the IDE.
     - Install dependencies using the IDE’s package manager or a GUI tool, referencing `requirements.txt`.
   - **Required Packages**:
     ```
     numpy
     opencv-python
     matplotlib
     torch
     torchvision
     tqdm
     pandas
     seaborn
     scikit-learn
     albumentations
     timm
     pillow
     ```

3. **Prepare Data**:
   - Place ultrasound images in `data/raw_data/images/`.
   - Place annotated images in `data/raw_data/annotated_data/images/`.
   - Place the label CSV (`labell.csv`) in `data/raw_data/annotated_data/`.
   - For Google Colab, store data in Google Drive (e.g., `/content/drive/MyDrive/Datasets/Projec_Unetbased/`) and update script paths accordingly.

## Running Experiments

- **Generate Masks**:
  - Upload `generate_masks.py` to Google Colab or open in a local IDE.
  - Run to convert annotated images to binary masks.
  - Output: Masks in `data/raw_data/masks/`.
  - Colab example: `!python /content/drive/MyDrive/Datasets/Projec_Unetbased/scripts/generate_masks.py`

- **Train Teacher Model**:
  - Upload `train_teacher_model.py` to Colab or open in an IDE.
  - Run to train a U-Net teacher model on annotated data.
  - Output: Model weights in `results/models/`.
  - Note: Complete the data loading and training loop sections.

- **Train Student Model**:
  - Upload `train_student_model.py` to Colab or open in an IDE.
  - Run to generate pseudo-labels and train a student U-Net model.
  - Output: Pseudo-labels in `data/pseudo_masks/` and model weights in `results/models/`.
  - Note: Implement pseudo-label generation and data loading.

- **Segment Kidneys**:
  - Upload `segment_kidneys.py` to Colab or open in an IDE.
  - Run to extract segmented kidneys using masks.
  - Output: Segmented images in `data/segmented_kidneys/`.

- **Classify Kidney Conditions**:
  - Upload `kidney_disease_classification_unet.py` to Colab or open in an IDE.
  - Run to train classifiers (e.g., ResNet50) on segmented kidneys.
  - Output: Metrics and visualizations in `data/classification_outputs/ssmunet_based/stage3_final_results/`.
  - Note: Complete the dataset and training loop sections.

## Results

Models saved in `results/models/`. Metrics and visualizations in `results/metrics/`, `results/visualizations/`, and `data/classification_outputs/ssmunet_based/stage3_final_results/` (CSV, text, PNG).

## License

This project is licensed under the MIT License. During review, access is restricted to authorized reviewers.
