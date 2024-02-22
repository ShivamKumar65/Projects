The objective of this project was to identify AI-generated text vs. human written text. The problem statement is as follows: Can you predict the 'ind' (0= human, 1 = AI) as a function of the 768 document embeddings, the word count and the punctuation?

All text data was converted into embeddings and the project further details the outcomes of this endeavour. Below are some comments that arose during this project.

Conclusion Comments:

1. At the project's outset, our initial model run involved selecting predictors with a substantial correlation (greater than 0.15, positive or negative) with the target variable. However, employing a dense layer neural network resulted in an F1 score of around 0.6. This prompted a realization that retaining a significant number of predictor variables might be essential, leading us to reconsider the strategy of dropping numerous predictors.

2. In a subsequent trial, we explored feature engineering by selecting the top 85% (and various other percentages) of features based on their importance in a Random Classifier Model. Despite these efforts, the model's performance did not significantly improve, maintaining an F1 score ranging between 0.6 and 0.68. Consequently, we chose not to proceed with a model incorporating feature engineering.

3. Following that, we developed a model while retaining all features, consisting of three densely connected layers with 50, 25, and 10 neurons, each using ReLU activation functions. After each dense layer, a dropout layer with a dropout rate of 0.5 was incorporated. The output layer utilized a sigmoid activation function with one output node. Notably, the model incorporated an early stopping callback with a patience of 60. Ultimately, this model achieved an F1 score of 0.7386 on the test partition.

4. The model exhibits robust performance in accurately identifying instances of the majority class (Human, Class 0), evidenced by a high true negative count (1004) and a low false positive count (6). Challenges arise in predicting instances of the minority class (AI, Class 1), reflected in a lower true positive count (65) and a slightly higher false negative count (40). This suggests the model's cautious approach, aiming to minimize false positives, aligning with the chosen dropout rate's regularization effect during training.

5. An Area Under the Curve (AUC) value of 0.94 in the Receiver Operating Characteristic (ROC) curve indicates the model's strong discriminative power. A higher AUC value implies better discrimination between positive and negative instances. The high AUC of 0.94 suggests the model performs exceptionally well in distinguishing between the two classes, affirming its robust predictive capability.

6. In conclusion, initial attempts to select predictors based on correlation yielded a neural network with a modest F1 score of 0.6, prompting reconsideration of feature reduction. Subsequent feature engineering efforts, despite not significantly improving model performance, informed the decision to retain all features. The final model, a three-layer dense neural network, exhibited robust performance with an F1 score of 0.7386 on the test partition and a strong AUC of 0.94 in the ROC curve, emphasizing its effectiveness in distinguishing between classes. Overall, this model effectively classifies instances as Human and AI.
