# DR-GAN: Conditional GAN for Fine-Grained Diabetic Retinopathy Lesion Synthesis  

## Overview  
This project implements a **Conditional Generative Adversarial Network (GAN)** for synthesizing high-resolution (1280x1280) fundus images with controllable diabetic retinopathy (DR) severity levels and lesion details. The synthesized images can augment training datasets for DR grading and lesion segmentation models, enhancing their performance in real-world applications.  

## Key Features  
- **Conditional GAN architecture** for DR image synthesis.  
- Multi-scale spatial and channel attention mechanisms.  
- Controllable DR severity grading (0-4).  
- Fine-grained lesion synthesis for realistic fundus images.  
- High-resolution image generation (1280x1280 pixels).  
- Multi-scale discriminators for robust adversarial training.  

---

## Project Structure  
```plaintext
dr-gan-project/
├── configs/          # Configuration files  
├── data/  
│   ├── raw/          # Original downloaded data  
│   └── processed/    # Preprocessed data  
├── notebooks/        # Jupyter notebooks for exploration  
├── src/  
│   ├── data/         # Data processing scripts  
│   ├── models/       # Model architectures  
│   └── utils/        # Utility functions  
├── tests/            # Unit tests  
└── requirements.txt  # Project dependencies  
```  

---

## Installation  

### 1. Clone the repository  
```bash  
git clone https://github.com/yourusername/dr-gan-project.git  
cd dr-gan-project  
```  

### 2. Set up a virtual environment  
**For Windows:**  
```bash  
python -m venv venv  
.\venv\Scripts\activate  
```  
**For Unix/MacOS:**  
```bash  
python -m venv venv  
source venv/bin/activate  
```  

### 3. Install dependencies  
```bash  
pip install -r requirements.txt  
```  

### 4. Configure Kaggle API  
1. Place your Kaggle API credentials in `~/.kaggle/kaggle.json`.  
2. Set appropriate file permissions:  
   ```bash  
   chmod 600 ~/.kaggle/kaggle.json  
   ```  

---

## Dataset  

The project uses the **IDRID dataset**, which includes:  
- 516 high-resolution fundus images.  
- DR severity grades (0-4).  
- Lesion segmentation masks.  
- Image resolution: 1280x1280 pixels.  

### Download the dataset  
```bash  
python src/data/download_data.py  
```  

---

## Model Architecture  

### Generator  
- Accepts conditional inputs: structural masks, lesion masks, and grading vectors.  
- Utilizes multi-scale spatial and channel attention mechanisms.  
- Progressive upsampling for high-resolution image generation.  
- Supports controllable DR severity grade synthesis.  

### Discriminator  
- Multi-scale patch-based architecture.  
- Capable of auxiliary classification for DR grading.  

---

## Training Pipeline  

### 1. Data Preprocessing  
- Image normalization.  
- Mask generation.  
- Data augmentation.  
- Grade encoding.  

### 2. Training Phases  
- **Generator pretraining**.  
- **Discriminator pretraining**.  
- **Joint adversarial training**.  
- **Fine-tuning** with attention modules.  

### 3. Loss Functions  
- **Adversarial loss**: For realism.  
- **Feature matching loss**: For generator stability.  
- **Perceptual loss**: For high-quality synthesis.  
- **Grading classification loss**: For accurate DR grading.  

---

## Usage  

### 1. Configure settings  
Copy and edit the example configuration file:  
```bash  
cp configs/config.example.yaml configs/config.yaml  
```  

### 2. Train the model  
```bash  
python src/train.py --config configs/config.yaml  
```  

### 3. Generate images  
```bash  
python src/generate.py --checkpoint path/to/checkpoint --output output/dir  
```  

---

## Evaluation Metrics  

- **Fréchet Inception Distance (FID)**: Measures image realism.  
- **Inception Score (IS)**: Evaluates diversity of generated images.  
- **DR Grading Accuracy**: Assesses the accuracy of DR severity predictions.  
- **Lesion Segmentation IoU**: Quantifies lesion segmentation performance.  
- **Clinical Expert Assessment**: Ensures clinical viability of synthesized images.  

---

## Results  

| Metric                  | Score       |  
|--------------------------|-------------|  
| **FID Score**            | X           |  
| **Inception Score**      | Y           |  
| **DR Grading Accuracy**  | Z%          |  

For qualitative analysis, refer to sample images [here](#).  

---

## Citation  

If you use this project, please cite:  

```bibtex  
@article{zhou2019dr-gan,  
  title={DR-GAN: Conditional Generative Adversarial Network for Fine-Grained Lesion Synthesis on Diabetic Retinopathy Images},  
  author={Zhou, Yi and Wang, Boyang and He, Xiaodong and Cui, Shanshan and Shao, Ling},  
  year={2019}  
}  
```  

---

## Contributing  

1. Fork the repository.  
2. Create a feature branch:  
   ```bash  
   git checkout -b feature/amazing-feature  
   ```  
3. Commit changes:  
   ```bash  
   git commit -m 'Add amazing feature'  
   ```  
4. Push the branch:  
   ```bash  
   git push origin feature/amazing-feature  
   ```  
5. Open a Pull Request.  

```
