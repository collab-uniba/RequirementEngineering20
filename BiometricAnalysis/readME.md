### Predicting Users’ Engagement during Interviews with Biofeedback and Supervised Learning: Replication Package



This package contains all the material used for the analysis presented in the paper  "Predicting Users’ Engagement during Interviewswith Biofeedback and Supervised Learning".

The scripts in the package can be used replicate the analysis described in the paper. In particular, the scripts can be used to:

- discretize the normalized score for valence and arousal in order to derive the labels

  ```
  Rscript Discretization.R Discretization.xlsx
  ```

  

- extract features from data collected using the Empatica E4 wristband

  ```
  Rscript Emotions.R
  ```

- concatenate the features of EDA, BVP, HR in one single dataset and add the columns with the valence and arousal labels. Three datasets will be created: 

  - Empatica_3labels, with all the instances
  - Empatica_2labels_valence, with all the instances having "positive" or "negative" as label
  - Empatica_2labels_arousal, with all the instances having "high or "low" as label

  ```
  Rscript concatenateDataset. R <input_dir> <labels_file>
  ```

- train the classification models for arousal and valence and compute the classification performance, using the Hold-out validation setting. The script for this analysis are included in the folder "Analysis". The input dataset used in this paper are: Empatica_2labels_arousal.csv and Empatica_2labels_valence.csv. <label> can assume "valence" or "arousal" as values, depending on the dataset chosen.

  ```
  nohup ./run_HoldOut.sh <input_dataset> models/models_all.txt <output_dir> E4 <label> &>log.txt &
  
  ```

  



