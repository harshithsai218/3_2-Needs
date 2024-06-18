# Train-Test Split Evaluation

![](img/2024-03-19-05-49-45.png)

The train-test split is a crucial technique for assessing the performance of a machine learning algorithm, applicable to both classification and regression tasks across various supervised learning algorithms. The process involves dividing a dataset into two distinct subsets: the training dataset and the test dataset.

The training dataset is utilized to train the machine learning model, allowing it to learn patterns and relationships within the data. Conversely, the test dataset remains untouched during the training phase. Instead, it serves as an unseen dataset to evaluate the trained model's performance. Here, the model takes input data from the test dataset, generates predictions, and compares them to the actual values, enabling an assessment of how well the model generalizes to new, unseen data.

The primary objective of this approach is to estimate the model's performance on new data that wasn't used during training. Essentially, it simulates real-world scenarios where the model needs to make predictions on unseen data. This ensures that the model's performance is not biased by the data it was trained on.

However, it's crucial to note that the train-test split procedure is most effective when dealing with sufficiently large datasets. This is because smaller datasets may not provide enough data for the model to learn effectively during training or to evaluate its performance accurately during testing.

![](img/2024-03-19-05-53-40.png)

To implement the train-test split in practice, various libraries such as `train_test_split` from `sklearn` can be used. These libraries facilitate the seamless partitioning of the dataset into training and testing subsets, ensuring that both sets contain a representative sample of data to train and evaluate the model effectively. Without an appropriate train-test split, the model may suffer from overfitting due to lack of data for training or underfitting due to inadequate evaluation on unseen data.


# Naïve Bayes Algorithm

### Overview
The Naïve Bayes algorithm is a probabilistic classifier based on Bayes' Theorem, which assumes independence among predictors. Despite this assumption, the algorithm performs well in many real-world situations, especially in text classification and spam filtering.

### Bayes' Theorem
Bayes' Theorem provides a way to calculate the probability of a hypothesis given prior knowledge. It is formulated as:

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

where:
- $P(A|B)$ is the probability of event A occurring given that B is true.
- $P(B|A)$ is the probability of event B occurring given that A is true.
- $P(A)$ is the probability of event A.
- $P(B)$ is the probability of event B.

### Naïve Bayes Classifier
The Naïve Bayes classifier applies Bayes' Theorem with the "naive" assumption of conditional independence between every pair of features given the class label. For a given data point described by features $X = (x_1, x_2, ..., x_n)$, the probability of it belonging to class $C$ is:

$$P(C|X) \propto P(C) \cdot P(x_1|C) \cdot P(x_2|C) \cdot ... \cdot P(x_n|C)$$

This simplifies the calculation and makes the algorithm scalable.

#### Steps in Naïve Bayes Classification
1. **Calculate Prior Probability**: Compute the prior probability for each class based on the training data.
2. **Likelihood Calculation**: For each feature, compute the likelihood of that feature given each class.
3. **Posterior Probability**: Use Bayes' Theorem to calculate the posterior probability for each class.
4. **Class Prediction**: Assign the class with the highest posterior probability to the data point.

#### Example
Consider a dataset for classifying whether it is suitable to play golf based on weather conditions (outlook, temperature, humidity, windy). Using Naïve Bayes, the classification would involve:

- Calculating the prior probability of playing golf and not playing golf.
- Calculating the likelihood of each feature (e.g., sunny, cool, high humidity, no wind) given the two classes.
- Applying Bayes' Theorem to find the posterior probability for playing and not playing golf.
- Predicting the class with the highest posterior probability.



# K-Nearest Neighbors (K-NN) Algorithm

#### Overview
K-NN is a simple, non-parametric, and lazy learning algorithm used for classification and regression. It works by finding the K closest data points (neighbors) in the training set and making predictions based on these neighbors.

#### Steps in K-NN
1. **Choose the Number of Neighbors (K)**: Select an appropriate value for K.
2. **Calculate Distance**: Compute the distance between the test data point and all training data points using a distance metric like Euclidean distance.
3. **Identify Neighbors**: Select the K data points that are closest to the test data point.
4. **Classify**: Determine the class of the test data point based on the majority class of the K nearest neighbors.

#### Example
Suppose we want to classify a new data point that looks similar to a cat or a dog. Our dataset contains images labeled as either cat or dog.

![](img/2024-06-18-17-35-44.png)

1. **Choose K**: Assume K=3.

2. **Calculate Distance**: Compute the Euclidean distance between the new image and all images in the training set.

![](img/2024-06-18-17-36-14.png)

3. **Identify Neighbors**: Suppose the 3 nearest neighbors consist of 2 images labeled as cat and 1 image labeled as dog.
4. **Classify**: The new image is classified as a cat because the majority of the 3 nearest neighbors are cats.

![](img/2024-06-18-17-38-28.png)

#### Advantages and Disadvantages of K-NN
- **Advantages**:
  - Simple and easy to implement.
  - No training period, making it a fast algorithm.
  - Can handle multi-class cases.

- **Disadvantages**:
  - Requires selection of K, which can be complex.
  - Computationally expensive, especially with large datasets.
  - Sensitive to the scale of the data and irrelevant features.


