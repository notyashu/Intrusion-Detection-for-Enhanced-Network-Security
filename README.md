# Intrusion Detection for Enhanced Network Security

This repository contains a comprehensive workflow for building and evaluating machine learning models to detect network intrusions, using the CIC IDS 2017 dataset from the University of New Brunswick (UNB).

## 📥 Original Dataset

- **CIC IDS 2017**: A modern benchmark dataset for intrusion detection, covering benign and various attack scenarios. Download from UNB:
  https://www.unb.ca/cic/datasets/ids-2017.html

## 📂 Raw Data Files

The raw CICIDS2017 CSV files required for preprocessing can be downloaded from the following Google Drive link:

[CSVs File Link](https://drive.google.com/drive/folders/1GtoNMR5SUJ81wkDLXINBwcJ8HtZbABhi?usp=sharing)

## 🚀 Project Structure

```
notyashu-intrusion-detection-for-enhanced-network-security/
├── README.md
├── LICENSE
├── importance_list_all_data.csv
├── importance_list_for_attack_files.csv
├── feature_pics/               # Important feature distribution visuals
├── 01_preprocessing.ipynb      # Data cleaning & encoding
├── 02_statistics.ipynb         # Descriptive statistics & EDA
├── 03_attack_filter.ipynb      # Filtering & labeling attack records
├── 04_1_feature_selection_for_attack_files.ipynb
├── 04_2_feature_selection_for_all_data.ipynb
├── 05_1_machine_learning_implementation_for_attack_files .ipynb
├── 05_2_machine_learning_implementation_with_18_feature.ipynb
├── 05_3_machine_learning_implementation_with_7_feature.ipynb
├── 05_4_machine_learning_implementation_final.ipynb
├── 05_5_ml_f_measure_comparison.ipynb
└── results/
    ├── results_1.csv
    ├── results_2.csv
    ├── results_3.csv
    ├── results_Final.csv
    ├── result_graph_1/         # Plots from experiment 1
    ├── result_graph_2/         # Plots from experiment 2
    ├── result_graph_3/         # Plots from experiment 3
    └── result_graph_Final/     # Final model performance graphs
```

## 📊 Workflow Overview

This project focuses on building an intrusion detection system using the CICIDS2017 dataset. The analysis pipeline consists of five sequential steps.  **Always run in numeric order**, as each step’s output feeds the next.:


1.  **Preprocessing ([01_preprocessing.ipynb](01_preprocessing.ipynb))**  
    - Cleans and merges the raw CICIDS2017 CSVs (from the `CSVs` folder) into a single `all_data.csv`.  
    - Handles missing values, type conversions, and label encoding.  
    - **Output:** `all_data.csv` (in project root).

2.  **Statistics ([02_statistics.ipynb](02_statistics.ipynb))**  
    - Loads `all_data.csv` and computes summary statistics of benign vs. attack records.  
    - Generates distribution plots for key features.  
    - **Note:** Informational only; does not feed later steps.

3.  **Attack Filtering ([03_attack_filter.ipynb](03_attack_filter.ipynb))**  
    - Splits `all_data.csv` into per-attack CSVs under `./attacks/`.  
    - For each of the 12 attack types, creates a file containing 30% attack samples + 70% benign.  
    - **Output:** 12 attack-specific CSVs in `attacks/`.  

4.  **Feature Selection**  
    - **[04_1_feature_selection_for_attack_files.ipynb](04_1_feature_selection_for_attack_files.ipynb)**  
      - For each attack-specific file, uses RandomForest to rank feature importances.  
      - Produces bar charts of top 20 features per attack.  
    - **[04_2_feature_selection_for_all_data.ipynb](04_2_feature_selection_for_all_data.ipynb)**  
      - Applies RandomForest-based importance ranking on the full `all_data.csv`.  
      - Produces a bar chart of the top 20 features overall.

5.  **Machine Learning Implementation**  
    Applies seven classifiers across various feature sets. Each notebook runs 10 trials, logs results to CSV, and saves box-and-whisker plots under `results/` subfolders.

    a.  **[05_1_machine_learning_implementation_for_attack_files .ipynb](05_1_machine_learning_implementation_for_attack_files .ipynb)**  
        - Uses top 4 features per attack (from step 4.1).  
        - Trains 7 algorithms on each attack file.  
        - **Outputs:** `results/results_1.csv` + plots in `results/result_graph_1/`.  

    b.  **[05_2_machine_learning_implementation_with_18_feature.ipynb](05_2_machine_learning_implementation_with_18_feature.ipynb)**  
        - Aggregates the 4 top features from each of 12 attacks → 48, dedupes to 18.  
        - Trains 7 algorithms on `all_data.csv` with these 18 features.  
        - **Outputs:** `results/results_2.csv` + plots in `results/result_graph_2/`.  

    c.  **[05_3_machine_learning_implementation_with_7_feature.ipynb](05_3_machine_learning_implementation_with_7_feature.ipynb)**  
        - Uses the top 7 features from step 4.2.  
        - Trains 7 algorithms on `all_data.csv`.  
        - **Outputs:** `results/results_3.csv` + plots in `results/result_graph_3/`.  

    d.  **[05_5_ml_f_measure_comparison.ipynb](05_5_ml_f_measure_comparison.ipynb)**  
        - Compares F-measure of NB, QDA, and MLP to identify their optimal feature sets.  
        - **Output:** Summary printed and saved to `results/`.  

    e.  **[05_4_machine_learning_implementation_final.ipynb](05_4_machine_learning_implementation_final.ipynb)**  
        - For NB, QDA, MLP uses features from the F-measure comparison; for others uses top 7 from step 4.2.  
        - Final 7-model evaluation on `all_data.csv`.  
        - **Outputs:** `results/results_Final.csv` + plots in `results/result_graph_Final/`.  



## 📈 Results

- Performance metrics (accuracy, precision, recall, F1-score) saved in `results_Final.csv`.
- Visual comparisons in `result_graph_Final/`.
- Feature importance lists:  `importance_list_all_data.csv`, `importance_list_for_attack_files.csv`.

## 📝 How to Reproduce

1. Download the CIC IDS 2017 dataset and place CSV files in a local `CSVs/` folder or use the provided Google Drive link.
2. Open and run notebooks in numerical order (01 → 05).
3. Review outputs in the `results/` directory.

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---
*Enhancing network security through data-driven intrusion detection.*
