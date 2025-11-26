# CONDOR EAS Reconstruction: CNN-Transformer Hybrid Model

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17717722.svg)](https://doi.org/10.5281/zenodo.17717722)

This repository contains the official implementation of the code and datasets used in the paper **"Deep learning for extensive air showers reconstruction at the CONDOR Observatory: A multi-task interpretable CNN-Transformer approach"** (2025).

The project implements a multi-task Deep Learning model combining **Convolutional Neural Networks (CNNs)** and **Transformers** to process signals from the CONDOR scintillation detector array. The model performs three simultaneous tasks:
1. **Gamma/Hadron Discrimination:** Separation between primary photons and protons.
2. **Angular Reconstruction:** Estimating the arrival direction (zenith angle) of the cosmic ray.
3. **Energy Estimation:** Inferring the energy of the primary particle.

## 📂 Repository Structure

- **`CONDOR_EAS-Reconstruction.ipynb`**: The main notebook containing the model architecture definition, training pipeline, validation, and metric evaluation.
- **`CONDOR_EAS-Data-Visualization.ipynb`**: Notebook for Exploratory Data Analysis (EDA), generating the paper's plots, and visualizing detector responses.
- **`CONDORPROCESSING_MULTI.py`**: Preprocessing script to convert raw CORSIKA simulation outputs into the structured dataset (`.pkl`) required by the neural network.
- **`requirements.txt`**: List of Python dependencies required to reproduce the environment.
- **`LICENSE`**: MIT License terms.

## 🚀 Installation & Requirements

This project requires **Python 3.9+**. We recommend setting up a virtual environment.

1. **Clone the repository:**
   ```bash
   git clone https://github.com/luisnavarrof/CONDOR_EAS-Reconstruction.git
   cd CONDOR_EAS-Reconstruction
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
   *Note: The `panama` library is required for reading CORSIKA files during the preprocessing stage.*

## 📊 Data Availability & Preprocessing

The processed datasets and trained models are hosted on Zenodo to ensure reproducibility.

### Option A: Using Preprocessed Data (Recommended)
1. **Download the dataset:**
   - Go to the Zenodo record: [**https://doi.org/10.5281/zenodo.17717722**](https://doi.org/10.5281/zenodo.17717722)
   - Download `processed_all_data.pkl`.
   - (Optional) Download `pipeline_artifacts.zip` if you want to use the pre-trained models.

2. **Setup:**
   - Place `processed_all_data.pkl` in the root directory of this repository.
   - If using artifacts, unzip `pipeline_artifacts.zip` into a folder named `pipeline_artifacts/`.

### Option B: Generating Data from Scratch
If you have the raw CORSIKA simulation files, you can regenerate the dataset:
1. Open `CONDORPROCESSING_MULTI.py`.
2. Update the input paths to point to your local CORSIKA files.
3. Run the script: `python CONDORPROCESSING_MULTI.py`.

## 💻 Usage

### 1. Data Visualization
To explore the dataset distributions, detector hitmaps, and signal characteristics:
- Open and run `CONDOR_EAS-Data-Visualization.ipynb`.

### 2. Model Training & Evaluation
To train the CNN-Transformer model from scratch:
- Open `CONDOR_EAS-Reconstruction.ipynb`.
- Ensure the `CACHE_FILE` path points to your `processed_all_data.pkl`.
- Run all cells.

## 📝 Citation

If you use this code or methodology in your research, please cite our paper and dataset:

```bibtex
@article{navarro2025cnn_transformer,
  title={Deep learning for extensive air showers reconstruction at the CONDOR Observatory: A multi-task interpretable CNN-Transformer approach},
  author={Navarro, Luis and Pezoa, Raquel and Viaux, Nicolás and Tapia, Sebastián},
  journal={Astronomy & Computing},
  year={2025},
  note={Preprint}
}

@dataset{navarro_2025_condor_data,
  author={Navarro, Luis},
  title={Dataset and Trained Models for CONDOR EAS Reconstruction (CNN-Transformer)},
  year={2025},
  publisher={Zenodo},
  doi={10.5281/zenodo.17717722},
  url={https://doi.org/10.5281/zenodo.17717722}
}
```

## ⚖️ License

This project is licensed under the MIT License - see the LICENSE file for details.
