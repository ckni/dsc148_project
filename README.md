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
Airlines can be compared to rank performance based on cancellations and delays, but this is not inherently a predictive task.

### Observing "Types" of Delay
Delay information can be binned to create a categorical feature. Bins can be subjectively defined. Intuition most likely suggests something along the lines of <30min, <1hr, <2hr, <3hr, <5hr, >5hr. Data can be plotted to determine best structure for binning. Alternatively, quantiles or percentiles could be used for binning. From there, a model can be built to predict delay type based on select features.

#### Note on delay related features
There are two main features in the dataset for delay: arrival delay and departure delay. Either one can be used for our purposes, but it makes more sense from a practical standpoint to use departure delay as that is the value that corresponds most strongly to the impact of delays on passengers.

## Determining Model
Part of this project will be determining what type of model to build for our predictive task. To this end, the most straightforward approach would be to run some preliminary tests on a selection of multiple models and determine which one or ones perform the best. Cross validation can be used to define the best model.
