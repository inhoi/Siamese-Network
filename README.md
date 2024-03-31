# Siamese Network

## Zero-Shot Learning
Zero-shot learning involves training a model to generalize to new categories without any training samples. It aims to recognize objects from unseen classes by learning intermediate semantic layers and properties. This approach saves time and effort in data labeling by providing high-level descriptions of new categories, allowing the model to relate them to known categories. The process consists of two stages: training, where semantic attributes are captured, and inference, where these attributes are used to predict new classes based on their initial attribute signatures.

## One-Shot Learning
One-shot learning requires minimal data to identify similarities between objects. It relies on a single instance or a few examples for each category to train the model. The goal is to enable the model to recognize features of an object and use prior knowledge to classify new objects. This technique is particularly useful in computer vision, facial recognition, and passport identification, where accurate classification with minimal data is crucial. Siamese networks are commonly used in one-shot learning.

## Few-Shot Learning
Few-shot learning involves training models with very little data, reducing the need for extensive data collection and computational resources. It is useful when there is insufficient data for traditional machine learning methods. Few-shot learning can be approached at the data level, by adding more data to a large base dataset, or at the parameter level, by limiting parameter space and using regularization to prevent overfitting. OpenAI's GPT-3 is an example of a few-shot learner.

### Differences

* Few-shot learning is suitable for scenarios with a small amount of data, and is used in applications like image classification and facial recognition.
* One-shot learning uses even less data, often just one example per category, making it ideal for tasks like identifying individuals in identification documents.
* Zero-shot learning is applicable when no training data is available for certain classes, allowing the model to classify objects it has never seen before.


## Limitations of Supervised Learning

* Supervised learning involves memorizing patterns in training data.
* Requires a large amount of labeled data for generalization.
* Performance may suffer when faced with new, unseen data.
* Alternative approaches: Unsupervised Learning, Semi-Supervised Learning, and Self-Supervised Learning.

## Semi-Supervised Learning

* Suitable when there is a small amount of labeled data and a large volume of unlabeled data.
* Applies supervised learning to labeled data and unsupervised learning to unlabeled data.
* Aims to improve generalization performance with minimal labeled data guidance.
* Decision boundary can be improved by modeling the distribution of data using unlabeled data.
* Objective function is the sum of supervised loss and unsupervised loss.

![image](https://github.com/inhoi/Siamese-Network/assets/76868046/fe25f8b1-6b48-4395-8117-9fa74d4f811d)

* Both supervised and unsupervised learning are conducted in one stage, unlike two-stage self-supervised learning and transfer learning.
* Supervised loss depends on whether the target is discrete (classification loss) or continuous (regression loss).
* Unsupervised loss is applied to unlabeled data to learn data characteristics.




