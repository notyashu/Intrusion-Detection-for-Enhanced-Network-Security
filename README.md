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

This project focuses on building an intrusion detection system using the CICIDS2017 dataset. The notebooks cover various stages of the process:

1. **Preprocessing ([01_preprocessing.ipynb](01_preprocessing.ipynb))**: Cleans and merges the CICIDS2017 CSV files, handling errors and inconsistencies.
2. **Statistics ([02_statistics.ipynb](02_statistics.ipynb))**: Performs statistical analysis and visualization on the preprocessed dataset.
3. **Attack Filtering ([03_attack_filter.ipynb](03_attack_filter.ipynb))**: Filters and separates specific attack types from the main dataset for focused analysis.
4. **Feature Selection**:
    * **[04_1_feature_selection_for_attack_files.ipynb](04_1_feature_selection_for_attack_files.ipynb)**: Selects relevant features specifically for the individual attack files created in the previous step.
    * **[04_2_feature_selection_for_all_data.ipynb](04_2_feature_selection_for_all_data.ipynb)**: Selects relevant features using the entire combined dataset.
5. **Machine Learning Implementation**:
    * **[05_1_machine_learning_implementation_for_attack_files .ipynb](05_1_machine_learning_implementation_for_attack_files.ipynb)**: Implements and evaluates various machine learning models on the filtered attack datasets using selected features.
    * **[05_2_ml_benign_dos.ipynb](05_2_ml_benign_dos.ipynb)**: Trains and evaluates models specifically for classifying Benign vs. DoS attacks.
    * **[05_3_ml_benign_portscan.ipynb](05_3_ml_benign_portscan.ipynb)**: Trains and evaluates models specifically for classifying Benign vs. PortScan attacks.
    * **[05_4_ml_benign_brute_force.ipynb](05_4_ml_benign_brute_force.ipynb)**: Trains and evaluates models specifically for classifying Benign vs. Brute Force attacks.
    * **[05_5_ml_f_measure_comparison.ipynb](05_5_ml_f_measure_comparison.ipynb)**: Compares the F-measure performance of the different machine learning models across the various classification tasks.

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

