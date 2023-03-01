# DSC 148 Final Project (Winter 2023)
Team Members: Chester Kai Ni, Sujay Talanki

## Dataset
Kaggle Dataset: https://www.kaggle.com/datasets/heemalichaudhari/airlines-delay

### Note on dataset storage
Due to the uncompressed dataset being >200MB and exceeding the GitHub file size limit, a compressed zip folder containing the dataset is included in the repository. Furthermore, a .gitignore file is included to ignore the uncompressed dataset file, which should be stored directly in the repository folder locally as DelayedFlights.csv.

# Early EDA

Exploring the dataset to build a research problem and get an idea of what the dataset looks like and how we could approach working with it.

TODO: Format this section into an introductory section in final paper, and include visualizations. Code for visualizations is not strictly necessary here.

## Determining Scope

### Observing Cancellations
General summary: 1.9m not cancelled, 600 cancelled. There are 3 types of cancellations (A, B, C), each corresponding to different reasons for cancellation. Portion of flights cancelled is too low, difficult to analyse.

### Observing Airlines
Airlines can be compared to rank performance based on cancellations and delays. For instance, average delay or median delay can be compared across airlines. However, this is not inherently a predictive task. 

### Observing "Types" of Delay
Delay information can be binned to create a categorical feature. Bins can be subjectively defined. Intuition most likely suggests something along the lines of <=30min, <=1hrs, <=2hrs, <=3hrs, <=5hrs, >5hrs. Data can be plotted to determine best structure for binning. Alternatively, quantiles or percentiles could be used for binning. From there, a model can be built to predict delay type based on select features. Binning the delay times creates a categorical feature, which turns this into a classification problem (as oppposed to regression).

#### Note on delay related features

#### Visualizing -- Pie Chart
Include pie chart here to show portion of flights in each category. Categories can be defined with indices (0-5; 0 lowest (<=30min), 5 highest (>5hr)).

Based on initial analysis, we find that ~2% of flights delayed for 3-5hrs and ~1% of flights delayed for >5hrs. As such, we modify our categories so that there are 4 total categories and the last one would be >3hrs.

#### Visualizing -- Correlation Matrix
Include correlation matrix here to show correlation between default features.

There are two main features in the dataset for delay: arrival delay and departure delay. Unsurprisingly, ArrDelay and DepDelay have a high correlation (0.95). A consideration should be made regarding which to use as our y-value. Initially it would appear to make more sense from a practical standpoint to use departure delay as that is the value that corresponds most strongly to the impact of delays on passengers. However, we could also take the mean of the two features to create a combined delay feature. Other options can be explored.

## Determining Model
Part of this project will be determining what type of model to build for our predictive task. To this end, the most straightforward approach would be to run some preliminary tests on a selection of multiple models and determine which one or ones perform the best. Cross validation can be used to define the best model.

### Types of Models
Some initial ideas: PCA, SVM. As is normal, the data should be standardize data and NaN values can be imputed with mean. Preprocessing steps can be set up via Sklearn preprocessing pipelines.

### Evaluating Models
A confusion matrix can be used to evaluate a predictive model for a categorical y-value.
