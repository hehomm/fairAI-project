# fairAI-project

## TO DO

- Preprocessing approach
- Combination of preprocessing and inprocessing
- Compare the models, maybe select just one
- Try with more protected attributes? Might be too hard

## Fairness measurements

from AI Fairness 360:
"There are two opposing worldviews on group fairness: we’re all equal (WAE) and what you see is what you get (WYSIWYG). -- If the application follows the WAE worldview, then the demographic parity metrics should be used: disparate_impact and statistical_parity_difference.  If the application follows the WYSIWYG worldview, then the equality of odds metrics should be used: average_odds_difference and average_abs_odds_difference."
- For example, average_odds_difference might be good, but requires class labels. We can easily turn regression results into classes by dividing them into bins. We have to decide what are our protected attributes and groups. Maybe racial minorities, or smaller income neighbourhoods?
- The false positive/negative parities could also be used by dividing the levels of vioolent crime into "high" and "low" categories. If our story is about building infrastructure etc, it's about assistive interventions, and therefore false negative parity could be good.
- https://aif360.readthedocs.io/en/stable/modules/sklearn.html#module-aif360.sklearn.metrics

The fairness-comparison library (https://github.com/algofairness/fairness-comparison) was also mentioned on the course and could be worth trying out. Not entirely sure what it measures though, probably a whole bunch of things.

Aequitas Bias Report (http://aequitas.dssg.io/) creates a whole report from data.

Additionally, we have to be careful of redlining happening since there are so many variables.

## Fitting fair ML models

### Preprocessing approach
TBA

### Inprocessing approach
Grid search reduction with bounded group loss constraint. Grid search reduction tries out different models and returns the one with smallest error, and bound group loss keeps the loss of each discrete group below a set value to avoid unfair contributions to the final model.

Linear regression:
- Because the original dataset was heavily curated (from 128 variables to 5) before fitting the linear regression, the inprocessing no longer does a lot. The final values mostly depend on whether or not the protected attribute is dropped from the data. In that sense, the end result is close to just careful manual preprocessing. Without feature selection, the results are fairly similar (a little worse).

Kernel ridge regression:
- For this model, all features are kept in the training data. Therefore, the grid search reduction has more room for improvement, and it reduces the effects of redlining that happens with highly correlated variables. Overall, this results in higher accuracy, although at the cost of higher unfairness.

### Postprocessing approach
AIF360 dies not offer any postprocessing tools that work with regression models.

## Story

possible options:
- companies investing in building housing, businesses, or other infrastructure in the safest areas

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
