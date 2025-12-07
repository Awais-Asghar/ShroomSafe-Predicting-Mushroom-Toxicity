# ShroomSafe: Predicting Mushroom Toxicity
![Project Status](https://img.shields.io/badge/Project_Status-Completed-brightgreen.svg)
![Models](https://img.shields.io/badge/Models-Decision_Tree_&_Random_Forest-orange.svg)
![Framework](https://img.shields.io/badge/Framework-Scikit_Learn-yellow.svg)
![Language](https://img.shields.io/badge/Language-Python-blue.svg)
![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)

# 1. Title

**ShroomSafe: Predicting Mushroom Toxicity**
Decision Tree and Random Forest based classification of edible and poisonous mushrooms.

---

# 2. Problem Statement

Wild mushrooms can be edible or poisonous. Many of them look very similar. For a normal person it is hard to tell which mushroom is safe and which is dangerous. The task is Given the physical features of a mushroom, predict if it is **edible** or **poisonous**. This is solved as a binary classification problem using Decision Tree and Random Forest models.

---

# 3. Motivation

* Mushroom poisoning can cause serious illness or even death.
* Visual inspection alone is risky because some edible and poisonous species look alike.
* The mushroom dataset is a classic example for learning classification, decision trees and feature importance.
* Decision Tree and Random Forest models are easy to interpret and work well with categorical features.

This project is mainly for learning and demonstration, not for real life medical use.

---

# 4. Dataset

**Source**
UCI Machine Learning Repository
Mushroom Classification Dataset
(you can also mention the Kaggle mirror if you used it)

**Size and classes**

* Total samples: 8124 mushrooms
* Two target classes

  * 0 or e: edible
  * 1 or p: poisonous

**Features**

All features are categorical. Some important ones:

* cap shape
* cap surface
* cap color
* bruises
* odor
* gill attachment, spacing, size, color
* stalk shape, root, surface above and below ring
* ring number and type
* spore print color
* population
* habitat

No missing values are present.

---

# 5. Exploratory Data Analysis

You plotted many bar charts to understand the distribution of each feature.

### 5.1 Class distribution

* Edible and poisonous classes are almost perfectly balanced.
  This means class imbalance is not a problem here.

### 5.2 Cap shape

Plots show that:

* Most mushrooms are **convex** or **flat**.
* Fewer mushrooms are **knobbed** or **bell shaped**.
* Very few are **sunken** or **conical**.

This helps understand which shapes are common in the dataset.

### 5.3 Odor

The odor distribution is very important.

* The most frequent odor is **none**.
* **Foul** odor is also very common.
* Other odors appear with smaller counts: **spicy**, **fishy**, **almond**, **anise**, **pungent**, **creosote**, **musty**.

From later analysis we see that odor is one of the strongest indicators of toxicity.

### 5.4 Other features

You also plotted the distribution for:

* cap surface and cap color
* presence of bruises
* gill attachment, spacing, size, color
* stalk shape, root, surface and color
* ring number and ring type
* spore print color
* population and habitat

These plots show that different categories of a feature have very different frequencies.
This also hints that some categories are strongly linked to edible or poisonous mushrooms.

---

# 6. Data Preprocessing

Steps used in the notebook:

1. Load the mushroom data into a DataFrame.
2. Encode all categorical columns to integers using LabelEncoder or similar method.
3. Separate features `X` and target label `y`.
4. Split the data into training and test sets, for example 80 percent train and 20 percent test.

No scaling is needed because all features are encoded categories, not continuous numbers.

---

# 7. Models

The project trains and compares two models.

## 7.1 Decision Tree Classifier

* Base model that learns simple if else rules from the data.
* Works very well with categorical features.
* Easy to visualize as a tree diagram.

Hyperparameters used in the notebook can be mentioned here
(for example criterion, max depth, min samples split).

You also exported and visualized the decision tree, which clearly shows splits such as odor, gill size and spore print color.

## 7.2 Random Forest Classifier

* Ensemble of many decision trees.
* Each tree is trained on a random subset of rows and columns.
* Final prediction is done by majority voting.
* More robust and less likely to overfit than a single tree.

Random Forest is used as the final model because it achieves the best performance.

---

# 8. Training and Evaluation

The encoded data is split into train and test sets.
Both Decision Tree and Random Forest are trained on the training set and evaluated on the test set.

Important metrics:

* Accuracy
* Precision
* Recall
* F1 score
* Confusion matrix

You can plug in the exact printed scores from your notebook for both models in this structure:

```text
Decision Tree:
  Accuracy:
  Precision:
  Recall:
  F1 Score:

Random Forest:
  Accuracy:
  Precision:
  Recall:
  F1 Score:
```

---

# 9. Random Forest Results

From the confusion matrix for Random Forest on the test set:

|                  | Predicted Edible (0) | Predicted Poisonous (1) |
| ---------------- | -------------------- | ----------------------- |
| True Edible 0    | 847                  | 0                       |
| True Poisonous 1 | 0                    | 778                     |

Total test samples = 847 + 778 = 1625.

So:

* Test Accuracy = **100 percent**
* Precision for edible class = 1.0
* Precision for poisonous class = 1.0
* Recall for both classes = 1.0
* F1 score for both classes = 1.0

This means Random Forest correctly classified every mushroom in the test set.

Note: Such perfect accuracy is possible on this dataset because the patterns are very strong, but in real world situations we still need to be careful about overfitting and dataset bias.

---

# 10. Feature Importance

Decision Tree based models can rank features by how much they reduce impurity.

Typically, the most important features in your notebook are:

* **odor**
* **gill size**
* **spore print color**
* possibly **stalk root** or similar features

These features are the main reasons why the model can clearly separate edible and poisonous mushrooms.

---

# 11. System Pipeline

You can draw this as a simple block diagram.

1. Load mushroom dataset
2. Explore distributions with bar charts
3. Encode categorical features to numeric labels
4. Split into train and test sets
5. Train Decision Tree and Random Forest models
6. Evaluate models using accuracy, F1 score and confusion matrix
7. Choose Random Forest as final model
8. Use model to predict toxicity for new mushroom samples

---

# 12. Limitations

* Dataset only covers specific mushroom species and conditions.
* All features are simple visual or physical traits; some real mushrooms require chemical or microscopic tests.
* Perfect performance on this dataset does not guarantee perfect performance in real forests.
* This project is for education, not for real life safety decisions.

---

# 13. Future Work

* Add cross validation to check stability of the model.
* Compare with other models such as Gradient Boosting or XGBoost.
* Build a small web app where a user can select mushroom features and see the prediction.
* Add SHAP or other explainability tools to show feature effects more clearly.
* Extend the project to multi class prediction between species instead of just edible vs poisonous.

---

# 14. Glossary

* **Decision Tree**
  A tree structure where each internal node is a test on a feature, branches are outcomes, and leaves are final classes.

* **Random Forest**
  An ensemble of many decision trees whose outputs are combined to get a stronger model.

* **Label Encoding**
  Converting category values to integer codes.

* **Impurity**
  Measure of how mixed the classes are in a node, often Gini index or entropy.

* **Confusion Matrix**
  Table that compares true labels with predicted labels.

---
