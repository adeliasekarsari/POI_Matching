# POI Matching Project

This repository contains scripts and models for Point of Interest (POI) Matching, covering tasks such as similarity classification and multi-label prediction of POI attributes.

---

## Files Overview

### 1. `Model Classification.ipynb`
This notebook processes and builds a POI similarity classification model using `sampling.xlsx` as input data.  

- **Input Features**:  
  - `distance_meters`  
  - `fuzzy`  
  - `jaccard`  
  - `tfidf_similarity`  
  - `levenshtein_similarity`  

- **Target Column**:  
  - Binary classification (`0` for non-similar, `1` for similar).  

- **Output**:  
  - Model: `model_v1.pkl`  
  - Algorithm: Tuned Random Forest  

- **Performance Metrics**:  
  - **Accuracy**:  
    - Train Set: 0.904  
    - Test Set: 0.933  
  - **Precision**:  
    - Train Set: 0.904  
    - Test Set: 0.933  
  - **Recall**:  
    - Train Set: 0.904  
    - Test Set: 0.933  
  - **F1-Score**:  
    - Train Set: 0.904  
    - Test Set: 0.933  

---

### 2. `Vector_Model_Building.ipynb`
This notebook develops a vectorization-based model to predict multiple POI attributes (`brand_name`, `category_name`, `group_name`, and `industry_name`) based on `poi_name`.  

- **Output**:  
  - Vectorizer: `poi_tfidf_vectorizer.pkl`  
  - Model: `poi_best_multioutput_model.pkl`  

---

### 3. `Model_Building_RND_Non_Specific.ipynb`
This notebook performs POI Matching using the previously trained `model_v1.pkl` on two datasets:  
  - `data_raw.xlsx`  
  - `data_internal.parquet`  

- **Process**:  
  1. Classifies POIs as either similar or non-similar using the classification model (`model_v1.pkl`).  
  2. For non-similar POIs (non-duplicates), predicts the following attributes:  
     - `brand_name`  
     - `category_name`  
     - `group_name`  
     - `industry_name`  

---

## Input Files

- **`sampling.xlsx`**: Contains sample data for training the similarity classification model.  
- **`data_raw.xlsx`**: Includes POI names and coordinates for matching.  
- **`data_internal.parquet`**: Additional POI data with similar structure as `data_raw.xlsx`.  

---

## Output Files

- **Classification Model**: `model_v1.pkl`  
- **Vectorizer**: `poi_tfidf_vectorizer.pkl`  
- **Multi-output Model**: `poi_best_multioutput_model.pkl`  
- **Classified Results**: Similar and non-similar POI classifications.  
- **Predicted Attributes**: Attribute predictions for non-similar POIs.  

---

## Project Highlights

- **Similarity Classification**: Achieved high performance metrics with a tuned Random Forest model.  
- **Attribute Prediction**: Developed an end-to-end solution for handling non-similar POIs by predicting key attributes.  
- **Scalability**: Designed for real-world applications, enabling efficient and accurate POI Matching.  

---

Feel free to explore the repository and raise issues or suggestions for improvement!
