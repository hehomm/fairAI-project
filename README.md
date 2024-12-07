# fairAI-project

## TO DO

- Preprocessing approach
- Combination of preprocessing and inprocessing
- Compare the models, maybe select just one
- Try with more protected attributes? Might be too hard

## Fairness measurements

From AI Fairness 360:
- Average odds difference
- False negative rate ratio

Both are group fairness metrics measured on classification results. The regression predictions are turned into classes by splitting them in half, with values under the median forming the class of low crime rate, and above the median values marked as high crime rate. The privileged group is communities with less than 20% population of black people, and unprivileged group with more than 20%.

## Fitting fair ML models

### Preprocessing approach
Tried two preprocessing methods, learning fair representations and disparate impact remover. Learning fair representations (LFR) works by encoding the data in a way that obfuscates the protected attributes, and disparate impact remover edits feature values to increase group fairness while preserving rank-ordering within groups.

Linear regression:
- LFT breaks the model completely. Linear regression is probably too simple to handle the obfuscated data. Disparate impact remover doesn't really improve fairness.

Kernel ridge regression:
- LFR works great. Disparate impact remover doesn't really improve fairness.

### Inprocessing approach
Grid search reduction with bounded group loss constraint. Grid search reduction tries out different models and returns the one with smallest error, and bound group loss keeps the loss of each discrete group below a set value to avoid unfair contributions to the final model.

Linear regression:
- Because the original dataset was heavily curated (from 128 variables to 5) before fitting the linear regression, the inprocessing no longer does a lot. The final values mostly depend on whether or not the protected attribute is dropped from the data. In that sense, the end result is close to just careful manual preprocessing. Without feature selection, the results are fairly similar (a little worse).

Kernel ridge regression:
- For this model, all features are kept in the training data. Therefore, the grid search reduction has more room for improvement, and it reduces the effects of redlining that happens with highly correlated variables. Overall, this results in higher accuracy, although at the cost of higher unfairness.

### Postprocessing approach
AIF360 dies not offer any postprocessing tools that work with regression models.

## Story
Companies investing in building housing, businesses, or other infrastructure in the safest areas. Unfairness then shows as

## Presentations

- First one: [https://docs.google.com/presentation/d/1pYw7V8xL8oRwKs4zzcJOEkoRiI3z5sbZ8G5j6GjraIY/edit?usp=sharing]
- Second one: [https://docs.google.com/presentation/d/1OVilFk7NHmO5UUIsb9rnH0NfBL1UjMqhEJ7jwBjYHVY/edit?usp=sharing]
    - Content:
        - Manual feature selection
        - Preprocessing
        - Inprocessing
        - Combination of all three

## Links
- dataset: [https://archive.ics.uci.edu/dataset/183/communities+and+crime]
- examples using this dataset: [https://github.com/vbordalo/Communities-Crime/tree/master] and [https://github.com/jwhabi/Communites-and-Crime]
