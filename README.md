# 🎬 Movie Review Sentiment Analysis

<div align="center">

[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.16.1-orange?style=for-the-badge&logo=tensorflow)](https://www.tensorflow.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-red?style=for-the-badge&logo=streamlit)](https://streamlit.io/)
[![Deep Learning](https://img.shields.io/badge/Deep%20Learning-LSTM%2FRNN-brightgreen?style=for-the-badge)](https://en.wikipedia.org/wiki/Deep_learning)

**A powerful deep learning application for sentiment analysis of movie reviews using IMDB dataset**

</div>

---

## 📖 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Technical Details](#technical-details)
- [Installation](#installation)
- [Usage](#usage)
- [Model Architecture](#model-architecture)
- [Dataset Information](#dataset-information)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

This project implements a **Recurrent Neural Network (RNN)** based sentiment analysis system that classifies movie reviews from the IMDB dataset as either **positive** or **negative**. The model is trained using word embeddings and SimpleRNN layers, and is made accessible through an intuitive **Streamlit web application**.

**Key Highlights:**
- ✨ Binary sentiment classification with high accuracy
- 🧠 Deep learning model using TensorFlow/Keras
- 🎨 Interactive Streamlit web interface
- 📊 Comprehensive Jupyter notebooks for training and experimentation
- 🚀 Easy-to-use prediction system

---

## ✨ Features

- **Advanced NLP Processing**: Word embedding and sequence padding for text preprocessing
- **SimpleRNN Model**: Lightweight yet effective RNN architecture for sequence learning
- **Pre-trained Model**: Ready-to-use trained model for immediate predictions
- **Web Interface**: User-friendly Streamlit application for real-time sentiment analysis
- **IMDB Integration**: Leverages the official IMDB dataset for training
- **Real-time Predictions**: Get instant sentiment scores with confidence levels
- **Jupyter Notebooks**: Detailed training and exploration notebooks included

---

## 📁 Project Structure

```
Movie-review-prediction/
├── main.py                          # Streamlit application for predictions
├── requirements.txt                 # Python dependencies
├── .gitignore                       # Git ignore rules
├── README.md                        # Project documentation (this file)
├── models/                          # Pre-trained models directory
│   └── (trained models stored here)
└── notebook/                        # Jupyter notebooks for development
    ├── 01_embedding.ipynb          # Word embedding and data exploration
    ├── 02_simplernn.ipynb          # SimpleRNN model training and evaluation
    └── prediction.ipynb             # Prediction examples and testing
```

---

## 🔬 Technical Details

### Technologies Used

| Component | Version | Purpose |
|-----------|---------|---------|
| **TensorFlow** | 2.16.1 | Deep learning framework |
| **Python** | 3.8+ | Programming language |
| **Streamlit** | Latest | Web application framework |
| **NumPy** | Latest | Numerical computing |
| **Pandas** | Latest | Data manipulation |
| **Scikit-learn** | Latest | Machine learning utilities |
| **Matplotlib** | Latest | Data visualization |

### Model Architecture

```
Input Layer (Word Indices)
        ↓
Embedding Layer (128 dimensions)
        ↓
SimpleRNN Layer (32 units)
        ↓
Dense Layer (16 units, ReLU activation)
        ↓
Output Layer (1 unit, Sigmoid activation)
        ↓
Binary Classification (Positive/Negative)
```

### Key Components

1. **Embedding Layer**: Converts integer sequences to dense vectors
2. **SimpleRNN**: Processes sequences with recurrent connections
3. **Dense Layers**: Fully connected layers for classification
4. **Sigmoid Activation**: Outputs probability between 0 and 1

---

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip package manager
- Git (for cloning the repository)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/harirajharsh8795/Movie-review-prediction.git
   cd Movie-review-prediction
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   
   # On Windows
   venv\Scripts\activate
   
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Verify installation**
   ```bash
   python -c "import tensorflow; print(tensorflow.__version__)"
   ```

---

## 💻 Usage

### Running the Streamlit Application

```bash
streamlit run main.py
```

The application will open in your default web browser at `http://localhost:8501`

### Using the Web Interface

1. **Enter a movie review** in the text area
2. **Click the "Classify" button** to analyze the sentiment
3. **View the results**:
   - Sentiment classification (Positive/Negative)
   - Confidence score (0.0 to 1.0)

### Example Reviews

**Positive Review:**
```
This movie is absolutely fantastic! The cast was amazing and the 
storyline kept me engaged throughout. Highly recommended!
```

**Negative Review:**
```
Terrible movie. Poor acting, confusing plot, and waste of time. 
I don't recommend it to anyone.
```

### Programmatic Usage

```python
from main import preprocess_text, model
from tensorflow.keras.models import load_model

# Load your model
model = load_model('simple_rnn_imdb.h5')

# Preprocess review
review = "Amazing movie, loved every second!"
preprocessed = preprocess_text(review)

# Make prediction
prediction = model.predict(preprocessed)
sentiment = 'Positive' if prediction[0][0] > 0.5 else 'Negative'
confidence = prediction[0][0]

print(f"Sentiment: {sentiment}")
print(f"Confidence: {confidence:.4f}")
```

---

## 📊 Model Architecture Details

### Embedding Layer
- **Input**: Integer sequences (word indices)
- **Output Dimension**: 128
- **Purpose**: Convert sparse integer representations to dense embeddings

### SimpleRNN Layer
- **Units**: 32
- **Activation**: tanh (default)
- **Purpose**: Capture sequential patterns in text

### Dense Layers
- **Layer 1**: 16 units, ReLU activation with dropout
- **Layer 2**: 1 unit, Sigmoid activation (binary output)

### Training Configuration
- **Optimizer**: Adam
- **Loss Function**: Binary Crossentropy
- **Metrics**: Accuracy
- **Maximum Sequence Length**: 500 words
- **Batch Size**: 32
- **Epochs**: 10+

---

## 📈 Dataset Information

### IMDB Dataset
- **Total Reviews**: 50,000
- **Training Set**: 25,000 reviews
- **Test Set**: 25,000 reviews
- **Classes**: 2 (Positive: rating ≥ 7, Negative: rating ≤ 4)
- **Vocabulary Size**: ~88,000 unique words
- **Average Review Length**: ~230 words

### Data Preprocessing
- Reviews are indexed by word frequency
- Words are converted to integers (1-9999)
- Sequences are padded/truncated to 500 words
- Rare words (index < 3) are replaced with padding

---

## 📚 Jupyter Notebooks

### 01_embedding.ipynb
- IMDB dataset exploration
- Word embedding visualization
- Data preprocessing pipeline
- Vocabulary analysis

### 02_simplernn.ipynb
- SimpleRNN model building
- Model training and evaluation
- Performance metrics and visualizations
- Model saving and loading

### prediction.ipynb
- Testing on custom reviews
- Evaluation metrics
- Prediction examples
- Error analysis

---

## 📊 Results

### Model Performance
- **Training Accuracy**: ~85-90%
- **Validation Accuracy**: ~85-88%
- **Test Accuracy**: ~80-85%
- **Precision/Recall**: Balanced across classes

### Performance Metrics
```
Confusion Matrix:
                Predicted Negative    Predicted Positive
Actual Negative        [TN]                  [FP]
Actual Positive        [FN]                  [TP]

Metrics:
- Accuracy: (TP + TN) / Total
- Precision: TP / (TP + FP)
- Recall: TP / (TP + FN)
- F1-Score: 2 * (Precision * Recall) / (Precision + Recall)
```

---

## 🔧 Configuration

### Model Parameters
Edit the training parameters in the notebooks:
```python
max_words = 10000           # Vocabulary size
max_len = 500              # Maximum sequence length
embedding_dim = 128        # Embedding dimension
rnn_units = 32             # SimpleRNN units
epochs = 10                # Number of training epochs
batch_size = 32            # Batch size during training
```

### Streamlit Configuration
Modify `~/.streamlit/config.toml` for custom settings:
```toml
[theme]
primaryColor = "#FF6B6B"
backgroundColor = "#F5F5F5"
secondaryBackgroundColor = "#E0E0E0"
textColor = "#262730"
```

---

## 🐛 Troubleshooting

### Common Issues

**Issue**: Model file not found
```bash
# Solution: Ensure the model file is in the correct directory
ls models/
```

**Issue**: ImportError: tensorflow not found
```bash
# Solution: Reinstall dependencies
pip install --upgrade -r requirements.txt
```

**Issue**: Port 8501 already in use
```bash
# Solution: Run on different port
streamlit run main.py --server.port 8502
```

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/YourFeature`)
3. **Commit** your changes (`git commit -m 'Add YourFeature'`)
4. **Push** to the branch (`git push origin feature/YourFeature`)
5. **Open** a Pull Request

### Areas for Contribution
- [ ] Improve model accuracy
- [ ] Add more neural network architectures (LSTM, GRU, Transformer)
- [ ] Enhance UI/UX of Streamlit app
- [ ] Add multi-language support
- [ ] Implement real-time model updates
- [ ] Add visualizations and analytics
- [ ] Expand documentation

---

## 📝 License

This project is licensed under the **MIT License** - see the LICENSE file for details.

---

## 👨‍💻 Author

**Kaushal** (@harirajharsh8795)

---

## 🙏 Acknowledgments

- **IMDB Dataset**: Provided by Keras/TensorFlow
- **TensorFlow Community**: For excellent documentation
- **Streamlit**: For the amazing web framework
- **Contributors**: Thank you for your support!

---

## 📞 Support

- **Issues**: Open an issue on [GitHub Issues](https://github.com/harirajharsh8795/Movie-review-prediction/issues)
- **Discussions**: Join [GitHub Discussions](https://github.com/harirajharsh8795/Movie-review-prediction/discussions)
- **Email**: For direct inquiries

---

## 🔗 Useful Resources

- [TensorFlow Documentation](https://www.tensorflow.org/)
- [Keras API Reference](https://keras.io/)
- [Streamlit Documentation](https://docs.streamlit.io/)
- [IMDB Dataset Documentation](https://keras.io/api/datasets/imdb/)
- [NLP with Deep Learning](https://cs224d.stanford.edu/)

---

<div align="center">

**⭐ If you find this project helpful, please give it a star! ⭐**

[Back to Top](#-movie-review-sentiment-analysis)

</div>