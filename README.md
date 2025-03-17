# 🎵 Music Genre Classification using Machine Learning 🎵 
**Author:** Kim Jin </br>
**Date:** May 2023

## Project Overview  
This project explores **music genre classification** using machine learning techniques. The dataset consists of **50,000 songs** with various audio features, requiring careful preprocessing, dimensionality reduction, and model selection to achieve optimal classification performance.  

---

## Dataset & Preprocessing  
- **Dataset:** 50,000 songs with metadata and extracted audio features.  
- **Handling Missing Values:**  
  - Duration (`-1`), Instrumentalness (`0`), and Tempo (`"?"`) were replaced with their respective column means.  
- **Encoding Categorical Features:**  
  - **Key** (12 unique values) → One-hot encoded.  
  - **Mode** (Major/Minor) → Binary encoded.  
  - **Genre Labels** → Label encoded (0-9).  
- **Feature Selection:** Removed non-essential attributes such as song name, artist, and Spotify ID.  

---

## Model Selection & Dimensionality Reduction  
To optimize classification performance, I tested multiple **machine learning models** with and without **dimensionality reduction**:  

### **Step 1: Initial Model Performance**  
Before applying dimensionality reduction, I trained three models: **Random Forest, AdaBoost, and SVM**.  
- **Random Forest** performed well, achieving high AUC scores across genres.  
- **AdaBoost** was slightly less effective but still competitive.  
- **SVM** struggled due to high computational costs and long training times, making it impractical on the full dataset.  

### **Step 2: Applying Dimensionality Reduction**  
To improve efficiency and potentially boost model interpretability, I explored three techniques:  
- **Principal Component Analysis (PCA)**: Provided the best balance between dimensionality reduction and retained variance.  
- **t-SNE (t-distributed Stochastic Neighbor Embedding)**: Generated a highly compressed representation but resulted in poor classification performance due to information loss.  
- **UMAP (Uniform Manifold Approximation and Projection)**: Performed better than t-SNE but was still outperformed by PCA.  

### **Step 3: Final Model Choice**  
After testing the models on transformed data:  
- **PCA + Random Forest** delivered the best classification results, confirming the importance of both feature selection and model efficiency.  
- **UMAP showed potential** but did not outperform PCA.  
- **t-SNE was not viable** for this classification task due to its impact on AUC scores.  

### **Key Takeaways**  
**Dimensionality reduction significantly impacts model performance**, and PCA was the best choice for this dataset.  
**Random Forest outperformed other classifiers** after transformation, making it the optimal model.  
**Hyperparameter tuning further improved results**, but computational limitations required trade-offs.  

---

## Final Model & Optimization  
- **Chosen Approach:** **PCA + Random Forest** (best AUC performance).  
- **Hyperparameter Optimization:**  
  - **GridSearchCV** for AdaBoost (improved AUC by ~0.02).  
  - **RandomSearch** attempted for Random Forest, but manual tuning was ultimately more effective due to computation limits.  

---

## Next Steps  
- Experiment with deep learning models (**CNNs, LSTMs**) for improved classification.  
- Explore ensemble methods to combine multiple classifiers for robustness.  
- Scale the approach using **PySpark** for large datasets.  # MusicData_Classification
