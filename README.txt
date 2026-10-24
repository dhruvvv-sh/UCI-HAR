Project 13 - Edge-Based Human Activity Recognition
==================================================

Course: AI in IoT (AIoT) Research Activity, FISAC
Department: ICT - CCE B, MIT Manipal

Team
----
- Dhruv Sharma - 240953504
- Rahan S Krishna - 240953496
- Pramath Bhagawatha K. - 240953488

Project objective
-----------------
This project classifies six human activities from smartphone accelerometer and
gyroscope measurements using the UCI Human Activity Recognition Using
Smartphones dataset. Six supervised machine-learning models are compared using
the three evaluation criteria specified for project 13:

- Accuracy
- Macro F1-score
- Full-test-set batch inference time

The evaluated models are Logistic Regression, Decision Tree, Random Forest,
RBF-kernel Support Vector Machine, XGBoost, and k-Nearest Neighbours.

Dataset
-------
The dataset contains recordings from 30 volunteers aged 19-48 wearing a
Samsung Galaxy S II at the waist. Accelerometer and gyroscope measurements were
sampled at 50 Hz. Signals were divided into 2.56-second windows with 50%
overlap, and 561 normalized time- and frequency-domain features were extracted
from every window.

Dataset summary:

- Training windows: 7,352 from 21 subjects
- Test windows: 2,947 from 9 different subjects
- Features per window: 561, bounded within [-1, 1]
- Activities: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING,
  STANDING, and LAYING

The official subject-independent training/test split is retained. Prepared
features are loaded directly; the raw-signal preprocessing pipeline is not
re-executed by the notebook.

Project files
-------------
- project.ipynb: Data loading, model training, evaluation, plots, and analysis
- activity_labels.txt: Numeric activity IDs and activity names
- features.txt: Names of the 561 engineered features
- features_info.txt: Description of feature construction
- DATASET_README.txt: Original UCI dataset documentation and license notice
- train/: Official training features, labels, subject IDs, and inertial signals
- test/: Official test features, labels, subject IDs, and inertial signals

Software requirements
---------------------
The reported experiment used:

- Python 3.13.13
- scikit-learn 1.9.0
- XGBoost 3.3.0

The notebook also requires NumPy, pandas, Matplotlib, Seaborn, and Jupyter.
Install the packages in a clean virtual environment with:

    python3 -m venv .venv
    source .venv/bin/activate
    python3 -m pip install jupyter numpy pandas matplotlib seaborn scikit-learn xgboost

How to run
----------
1. Extract the ZIP archive without changing the folder structure.
2. Open a terminal in the extracted Project-13-UCI-HAR directory.
3. Create/activate the environment and install the packages shown above.
4. Start Jupyter:

       jupyter notebook project.ipynb

5. Run the notebook from the first cell downward. The official test set must
   remain unchanged.

Primary reported results
------------------------
The project compares fixed model configurations on the official test split.

Model                  Accuracy (%)   Macro F1 (%)
---------------------  ------------   ------------
Logistic Regression          96.064         96.056
Decision Tree                86.257         85.981
Random Forest                92.501         92.343
SVM (RBF)                    95.046         94.991
XGBoost                      93.180         93.102
KNN                          90.024         89.702

Logistic Regression achieved the highest accuracy and macro F1 and the lowest
measured batch prediction time among the six fixed configurations. These are
host-computer batch timings for all 2,947 test windows, not single-window,
smartphone, energy, feature-extraction, or end-to-end measurements.

The notebook may also contain clearly marked exploratory subject-wise
cross-validation and hyperparameter-search work. Those exploratory results are
not the fixed-configuration results in the primary table above and should not
be mixed with them.

Scope and limitations
---------------------
- Smartphone/edge deployment is proposed but was not implemented.
- Sensor acquisition, on-device feature extraction, networking, memory, and
  energy consumption were not measured.
- Timing depends on hardware, software versions, threading, and system load.
- The controlled dataset contains 30 participants and one phone position.
- Sitting and standing are the main source of classification confusion.

Dataset attribution and license notice
--------------------------------------
Dataset creators:
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto, and
Xavier Parra.

Required citation:
D. Anguita, A. Ghio, L. Oneto, X. Parra, and J. L. Reyes-Ortiz,
"A Public Domain Dataset for Human Activity Recognition Using Smartphones,"
21st European Symposium on Artificial Neural Networks, Computational
Intelligence and Machine Learning (ESANN), Bruges, Belgium, 2013, pp. 437-442.

UCI dataset DOI: https://doi.org/10.24432/C54S4K

The dataset is distributed AS-IS by its creators, with no implied or explicit
responsibility for its use or misuse. The original dataset notice states that
commercial use is prohibited and that publications must acknowledge the
dataset reference above. See DATASET_README.txt for the complete original
documentation.
