# Shill bidding detection 
Although shill bidding is a common auction fraud, it is however very tough to detect. The challenge is that the behavior of fraud bidders could be very similar to normal bidders. In this research project, I will implement an unsupervised learning algorithm for clustering and labeling of shill bidding using real business data.

The **challenge** of this experiment is the records whose present obvious features on normal or shill biddings. I labeled those data as 'suspicious' and used supervised classification to further split the 'suspicious' records. The training data for supervised classification were those clearly labeled normal and shill bidding records.

## Data
he data is real auction records from eBay, and is downloaded from [UCI](https://archive.ics.uci.edu/ml/datasets/Shill+Bidding+Dataset).

## Experiment procedure
#### Data preparation
I separate data based on auction duration into 5 groups.
#### Unsupervised clustering
I will test below unsupervised learning algorithms:
* K-means
* Agglomerative
* Gaussian Mixture
#### Labelling
I designed a "voting" algorithm to label the clusters:
1. for each auction duration group, calculate the mean value of all feature -- group mean
2. for each cluster, calculate the mean value for each feature -- feature mean
    if (feature mean > group mean): vote 1
    else: vote 0
3. for each cluster, sum the votes (total 8 features)
    if (vote > 4): Shill bidding
    if (vote < 4): Normal bidding
    else: Suspicious bidding
#### Supervised classification
I used the recognized normal and shill bidding as training set for modeling to further split the suspicious records

## Results
* _K_means_ is determined to have the best clustering performace.
* 6% records are recognized as shill bidding using unsupervised clustering.
* 28% records are recognized as suspicious bidding using unsupervised clustering.
* After supervised classification on suspicious bidding, totally **9%** records are recognized as shill bidding.

## More thinks for further improvement
* After being fed more data, this model should be able to predict shill bidding on eBay more efficiently.

## Presentation
https://github.com/zhaoxin1124ds/Shill-bidding-detection-/blob/main/Shill_bider_clustering.pdf
