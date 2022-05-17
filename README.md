```
           _   _  ____  __  __          _  __     __           
     /\   | \ | |/ __ \|  \/  |   /\   | | \ \   / /           
    /  \  |  \| | |  | | \  / |  /  \  | |  \ \_/ /            
   / /\ \ | . ` | |  | | |\/| | / /\ \ | |   \   /             
  / ____ \| |\  | |__| | |  | |/ ____ \| |____| |              
 /_/_ _ \_\_| \_|\____/|_|_ |_/_/ _ _\_\______|_| _ _ _        
 (_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_|_) _   _ 
 |  __ \|  ____|__   __|  ____/ ____|__   __|_   _/ __ \| \ | |
 | |  | | |__     | |  | |__ | |       | |    | || |  | |  \| |
 | |  | |  __|    | |  |  __|| |       | |    | || |  | | . ` |
 | |__| | |____   | |  | |___| |____   | |   _| || |__| | |\  |
 |_____/|______|  |_|  |______\_____|  |_|  |_____\____/|_| \_|
```                                                                                                                              
##### Anomalies. Anna Molly.
***
Anomaly Detection is the practice of identifying data points, items, observations or events that do not conform to the expected pattern of a given group.

### What are Anomalies?

- Anomaly - Anomalies are the unusual, unexpected, surprising patterns in the observed world. An anomalous data point is a deviation from a rule or from what is regarded as normal; an outlier. An anomaly is any event or measurement that is out of the ordinary regardless of whether it is exceptional or not.
- Outlier - An outlier is an observation that lies an abnormal distance from other values in a random sample from a population. In a sense, this definition leaves it up to the analyst (or a consensus process) to decide what will be considered abnormal. Before abnormal observations can be singled out, it is necessary to characterize normal observations. - [NIST/SEMATECH e-Handbook of Statistical Methods](https://www.itl.nist.gov/div898/handbook/prc/section1/prc16.htm)
- The terms "outlier" and "anomaly" are frequently used interchangeably.
- In some cases, statisticians sometimes use the term 'outlier' to mean "something I should remove from the dataset so that it doesn't skew my model I'm building".
- In other cases, we may reserve the word 'anomaly' for data points we want to keep because they are valuable if caught or costly if missed. It's also possible to have an anomaly that is an inlier, meaning that the data is anomalous in nature but is close (in distance) to the mean, mode, or expected grouping(s).
***
### The best way to detect anomalies is to know your domain

- For example, knowing that there is nothing colder than absolute zero degrees Kelvin informs how we approach an observation below 0 degrees Kelvin. It may mean that there is something wrong with the measuring tool or a clerical error like a typo (more likely).
- What determines if a data point is an outlier is a function of who determines if that data point is anomalous and why.
- One person's noise is another person's signal, depending on their goals and the costs and benefits to be gained/avoided from identifying that data point.
    - To one analyst aiming for a clean model of 50/50 chance, observing a flipped coin that lands exactly on its side is an anomaly may be noise that they should ignore from their model.
    - To another practitioner, the anomaly may be an observation of very high value that they want to catch, like early detection of a rare disease.
- Recall the e-Handbook of Statistical Methods definition an outlier: "an observation that lies an abnormal distance from other values in a random sample from a population. In a sense, this definition leaves it up to the analyst (or a consensus process) to decide what will be considered abnormal".
- It's important to define the criteria, the decision rule, for what makes an observation an inlier or an outlier.
- Usually, the deciding factor is cost/benefit analysis:
    - Is our goal to hunt for anomalies at all costs because lives are on the line?
    - Or do we do more good for people by producing a model that treats outliers as noise?
    - What is the cost of a false positive or a false negative?
    - What is the benefit of a true positive or a true negative?
***
### Outliers may contain important information

Outliers should be investigated carefully.

Often they contain valuable information about the process under investigation or the data gathering and recording process. Before considering the possible elimination of these points from the data, one should try to understand why they appeared and whether it is likely similar values will continue to appear. Of course, outliers are often bad data points.
***
### Types of Anomalies
- Use Cases: Response times (longer than usual), error rates (more than usual), network load, cyber intrusions, fraud.
- Point Anomalies: A single instance of data is anomalous if it's too far off from the rest. For example, detecting data exfiltration based on gigabytes leaving the network, detecting credit card fraud based on "amount spent", etc.
- Contextual Anomalies: The abnormality is context specific. This type of anomaly is common in time-series data. For example, accessing confidential files during work hours is normal, but in the middle of the night is odd.
- Collective Anomalies: A set of data instances collectively helps in detecting anomalies. For example, someone is trying to copy data form a remote machine to a local host unexpectedly, an anomaly that would be flagged as a potential cyber attack. The combination of the event from the remote machine and the event from the local host combine to detect the anomaly.
- Anomalies vs. Noise Removal vs. Novelty Detection: Novelty detection is concerned with identifying an unobserved pattern in new observations not included in training data — for instance, a sudden interest in a new channel on YouTube during Christmas. Noise Removal (NR) is the process of immunizing analysis from the occurrence of unwanted observations; in other words, removing noise from an otherwise meaningful signal.

https://www.datascience.com/blog/python-anomaly-detection
***
### Specific Techniques for Identifying/Detecting Anomalies

#### Statistical Methods

- Flag the data points that deviate from the expected, based on the statistical properties, such as mean, median, mode, and quantiles.
- You could define an anomalous data point as one that deviates by a certain standard deviation from the mean.
- You could use a simple or exponential moving average to smooth short-term fluctuations and highlight long-term ones.
- This method is challenging with really noisy data.

#### Support Vector Machine & Isolation Forest Anomaly Detection
- There are extensions to the supervised technique, such as OneClassSVM, that can be used to identify anomalies as an unsupervised problems (in which training data are not labeled).
- The algorithm learns a soft boundary in order to cluster the normal data instances using the training set, and then, using the testing instance, it tunes itself to identify the abnormalities that fall outside the learned region.
#### Clustering-Based Anomaly Detection
- Assumption: Data points that are similar tend to belong to similar groups or clusters, as determined by their distance from local centroids.
- K-means creates 'k' similar clusters of data points. Data instances that fall into abnormally small clusters could potentially be marked as anomalies.
- Using density based clustering, like DBSCAN, we can design the model such that the data points that do not fall into a cluster are the anomalies.
#### Density-Based Anomaly Detection

Assumption: Normal data points occur around a dense neighborhood and abnormalities are far away.
- The nearest set of data points are evaluated using a score, using one of two algorithms:
    - KNN: K-Nearest Neighbor
    - LOF: Local Outlier Factor, aka the relative density of data which is based on the reachability distance.
***
Remember

- There is not a magic algorithm that takes away our responsibility to think clearly and critically about why an observation is anomalous.
- There are no hard fast rules for whether or not an outlier should be ignored or investigated.
- The answer is "it depends", and the important part is identifying what that depends on, specifically.
***
Advice from Practitioners

"None of these methods will deliver the objective truth about which of a dataset’s observations are outliers, simply because there is no objective way of knowing whether something is truly an outlier or an honest-to-goodness data point your model should account for." - Colin Gorrie

"In my view, the more formal statistical tests and calculations are overkill because they can’t definitively identify outliers. Ultimately, analysts must investigate unusual values and use their expertise to determine whether they are legitimate data points." - Jim Frost

"One important reason to look into outliers is to correct errors in your data. There are two things we should never do with outliers. The first is to silently leave an outlier in place and proceed as if nothing were unusual. The other is to drop an outlier from the analysis without comment just because it's unusual." - K. Barkdo