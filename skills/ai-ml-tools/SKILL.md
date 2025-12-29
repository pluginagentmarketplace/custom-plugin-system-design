---
name: ai-ml-tools
description: Master AI and machine learning tools including TensorFlow, PyTorch, scikit-learn, LLMs, and prompt engineering. Use when building machine learning models, working with AI agents, or implementing data science solutions.
sasmp_version: "1.3.0"
bonded_agent: 01-frontend-web-development
bond_type: PRIMARY_BOND
---

# AI & Machine Learning Tools

## Quick Start

### Scikit-learn (Classic ML)
```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report

# Load and split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Train model
model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)

# Evaluate
y_pred = model.predict(X_test)
print(accuracy_score(y_test, y_pred))
print(classification_report(y_test, y_pred))
```

### TensorFlow/Keras
```python
import tensorflow as tf
from tensorflow import keras

# Build model
model = keras.Sequential([
    keras.layers.Dense(128, activation='relu', input_shape=(28*28,)),
    keras.layers.Dropout(0.2),
    keras.layers.Dense(64, activation='relu'),
    keras.layers.Dense(10, activation='softmax')
])

# Compile
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)

# Train
model.fit(X_train, y_train, epochs=10, validation_split=0.1)

# Evaluate
loss, accuracy = model.evaluate(X_test, y_test)
```

### PyTorch
```python
import torch
import torch.nn as nn

class NeuralNetwork(nn.Module):
    def __init__(self):
        super().__init__()
        self.linear1 = nn.Linear(28*28, 128)
        self.relu = nn.ReLU()
        self.linear2 = nn.Linear(128, 10)

    def forward(self, x):
        x = self.linear1(x)
        x = self.relu(x)
        x = self.linear2(x)
        return x

# Training loop
model = NeuralNetwork()
optimizer = torch.optim.Adam(model.parameters())
loss_fn = nn.CrossEntropyLoss()

for epoch in range(10):
    for X_batch, y_batch in train_loader:
        pred = model(X_batch)
        loss = loss_fn(pred, y_batch)
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
```

### Prompt Engineering with OpenAI
```python
import openai

response = openai.ChatCompletion.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Explain quantum computing in simple terms"}
    ],
    temperature=0.7,
    max_tokens=500
)

print(response.choices[0].message.content)
```

## Data Science Workflow

### 1. Data Loading & Exploration
```python
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('data.csv')

# Exploratory analysis
print(df.head())
print(df.info())
print(df.describe())

# Visualize
import matplotlib.pyplot as plt
plt.hist(df['column'])
plt.show()
```

### 2. Data Preprocessing
```python
from sklearn.preprocessing import StandardScaler, LabelEncoder

# Handle missing values
df.fillna(df.mean(), inplace=True)

# Encode categorical variables
le = LabelEncoder()
df['category'] = le.fit_transform(df['category'])

# Scale numerical features
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

### 3. Feature Engineering
```python
# Create new features
df['age_group'] = pd.cut(df['age'], bins=[0, 18, 35, 60, 100])

# Polynomial features
from sklearn.preprocessing import PolynomialFeatures
poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X)

# Feature selection
from sklearn.feature_selection import SelectKBest, f_classif
selector = SelectKBest(f_classif, k=10)
X_selected = selector.fit_transform(X, y)
```

## Machine Learning Algorithms

### Supervised Learning
- **Linear Regression**: Predicting continuous values
- **Logistic Regression**: Binary/multi-class classification
- **Decision Trees**: Interpretable non-linear models
- **Random Forest**: Ensemble of decision trees
- **Gradient Boosting**: XGBoost, LightGBM, CatBoost
- **SVM**: Support Vector Machines
- **KNN**: k-Nearest Neighbors
- **Neural Networks**: Deep learning models

### Unsupervised Learning
- **K-Means**: Clustering algorithm
- **Hierarchical Clustering**: Dendrogram-based clustering
- **DBSCAN**: Density-based clustering
- **PCA**: Dimensionality reduction
- **t-SNE**: Visualization of high-dimensional data
- **Autoencoders**: Neural network dimensionality reduction

## Deep Learning Architectures

### Computer Vision
- **CNN**: Convolutional Neural Networks
- **ResNet**: Residual networks
- **VGG**: Visual Geometry Group
- **YOLO**: Object detection
- **U-Net**: Image segmentation
- **Vision Transformer**: Attention-based image models

### Natural Language Processing
- **RNN/LSTM**: Sequence modeling
- **GRU**: Gated Recurrent Units
- **Transformers**: BERT, GPT, T5
- **Attention Mechanism**: Self-attention, multi-head attention
- **Embeddings**: Word2Vec, GloVe, FastText
- **Fine-tuning**: Transfer learning with LLMs

## LLM & Prompt Engineering

### Prompt Engineering Techniques
```python
# Few-shot learning
prompt = """
Translate English to French:
- Hello → Bonjour
- Goodbye → Au revoir
- Thank you → Merci

- Good morning →
"""

# Chain of Thought
prompt = """
Question: If there are 3 cars in a parking lot and 2 more arrive, how many cars are there?
Let me think step by step:
1. Initially: 3 cars
2. Arrive: 2 more cars
3. Total: 3 + 2 = 5 cars

Question: ...
"""

# Role-based prompting
prompt = """You are an expert data scientist. Analyze this dataset and provide insights..."""
```

### Popular LLM APIs
- **OpenAI**: GPT-4, GPT-3.5, Embeddings
- **Anthropic**: Claude API
- **Google**: PaLM, Gemini
- **Meta**: Llama
- **Hugging Face**: Open source models

## MLOps & Deployment

### Model Serving
- **FastAPI**: Serve ML models as APIs
- **TensorFlow Serving**: Production ML serving
- **MLflow**: Model tracking and deployment
- **BentoML**: Packaging and serving
- **Seldon Core**: ML model serving

### Monitoring & Tracking
- **MLflow**: Experiment tracking
- **Weights & Biases**: Model experiments
- **Neptune.ai**: Experiment management
- **DVC**: Data versioning
- **Model Registry**: Version control for models

## Resources

- **Scikit-learn**: https://scikit-learn.org/
- **TensorFlow**: https://tensorflow.org/
- **PyTorch**: https://pytorch.org/
- **Keras**: https://keras.io/
- **Hugging Face**: https://huggingface.co/
- **Fast.ai**: https://fast.ai/
- **Kaggle**: https://kaggle.com/
- **Papers with Code**: https://paperswithcode.com/

---

**See Also**: system-design, backend-frameworks
