# fairAI-project

## TO DO

- preprocess data
- fit machine learning models
    - select best one

## Fairness measurements

from AI Fairness 360:
"There are two opposing worldviews on group fairness: we’re all equal (WAE) and what you see is what you get (WYSIWYG). -- If the application follows the WAE worldview, then the demographic parity metrics should be used: disparate_impact and statistical_parity_difference.  If the application follows the WYSIWYG worldview, then the equality of odds metrics should be used: average_odds_difference and average_abs_odds_difference."
- For example, average_odds_difference might be good, but requires class labels. We can easily turn regression results into classes by dividing them into bins. We have to decide what are our protected attributes and groups. Maybe racial minorities, or smaller income neighbourhoods?
- The false positive/negative parities could also be used by dividing the levels of vioolent crime into "high" and "low" categories. If our story is about building infrastructure etc, it's about assistive interventions, and therefore false negative parity could be good.
- https://aif360.readthedocs.io/en/stable/modules/sklearn.html#module-aif360.sklearn.metrics

The fairness-comparison library (https://github.com/algofairness/fairness-comparison) was also mentioned on the course and could be worth trying out. Not entirely sure what it measures though, probably a whole bunch of things.

Aequitas Bias Report (http://aequitas.dssg.io/) creates a whole report from data.

Additionally, we have to be careful of redlining happening since there are so many variables.

## Story

possible options:
- hospitals deciding the number of emergency rooms or other specialized healthcare resources based on the number of violent crimes
- companies investing in building housing, businesses, or other infrastructure in the safest areas

## Presentations

I usually use Google Slides, e.g. this is a nice template: [https://docs.google.com/presentation/d/1pYw7V8xL8oRwKs4zzcJOEkoRiI3z5sbZ8G5j6GjraIY/edit?usp=sharing]

## Links
- dataset: [https://archive.ics.uci.edu/dataset/183/communities+and+crime]
- examples using this dataset: [https://github.com/vbordalo/Communities-Crime/tree/master] and [https://github.com/jwhabi/Communites-and-Crime]
