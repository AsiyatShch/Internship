This notebook represents the analytical study of different models and approaches

# The first part
Study on 1 dataset and different approaches of preprocessing:
 - scaling
 - selection of important features
 - smoothing
 - time shifting
 - removing outliers
 - smoting

Each method was evaluated with different models and then the best combination was chosen:
 - boosting
 - LSTM
 - Attention mechanism with LSTM
 - SVM
 - Stacking

Moreover, the study on complications based on the differentiation of neutral/thumb/other gestures was performed.

# The second part
The models with the highest f1 score were studied on all datasets.
This section shows the variability of data even in experiments of 1 pilote.
The effort to create a general model was done without success.
The study on optimization of pilote training was performed, we can assume that 30% of the previous time period is enough for calibration
