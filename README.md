# Siamese Network

## Zero-Shot Learning
Zero-shot learning involves training a model to generalize to new categories without any training samples. It aims to recognize objects from unseen classes by learning intermediate semantic layers and properties. This approach saves time and effort in data labeling by providing high-level descriptions of new categories, allowing the model to relate them to known categories. The process consists of two stages: training, where semantic attributes are captured, and inference, where these attributes are used to predict new classes based on their initial attribute signatures.

## One-Shot Learning
One-shot learning requires minimal data to identify similarities between objects. It relies on a single instance or a few examples for each category to train the model. The goal is to enable the model to recognize features of an object and use prior knowledge to classify new objects. This technique is particularly useful in computer vision, facial recognition, and passport identification, where accurate classification with minimal data is crucial. Siamese networks are commonly used in one-shot learning.

## Few-Shot Learning
Few-shot learning involves training models with very little data, reducing the need for extensive data collection and computational resources. It is useful when there is insufficient data for traditional machine learning methods. Few-shot learning can be approached at the data level, by adding more data to a large base dataset, or at the parameter level, by limiting parameter space and using regularization to prevent overfitting. OpenAI's GPT-3 is an example of a few-shot learner.

** Differences **

* Few-shot learning is suitable for scenarios with a small amount of data, and is used in applications like image classification and facial recognition.
* One-shot learning uses even less data, often just one example per category, making it ideal for tasks like identifying individuals in identification documents.
* Zero-shot learning is applicable when no training data is available for certain classes, allowing the model to classify objects it has never seen before.


## Limitations of Supervised Learning

* Supervised learning involves memorizing patterns in training data.
* Requires a large amount of labeled data for generalization.
* Performance may suffer when faced with new, unseen data.
* Alternative approaches: Unsupervised Learning, Semi-Supervised Learning, and Self-Supervised Learning.

![image](https://github.com/inhoi/Siamese-Network/assets/76868046/5d9bd2e4-eead-4aa1-99b2-6203adfdea48)

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

## Pairwise Learning

* models are trained using pairs of data.
* In the case of Siamese networks, pairs of images are used, which can be similar or different. When these image pairs are provided as input to the network, the network independently processes each image and then compares their features to calculate similarity.
* For example, consider using a Siamese network in a facial recognition system. In this scenario, two different facial images can be provided as input to the network. The network processes each image separately and compares their features to determine how similar they are. If the two images are of the same person's face, the network will judge the images to be similar; otherwise, it will judge them to be different.
* In this manner, Siamese networks learn the similarity between pairs of images, enabling the network to determine the similarity between images.

## Siamese Network

Siamese networks are known for their ability to perform one-shot learning, as they require only one training example for each class. The key feature of these networks is their ability to generate a similarity score between a reference image and a test image. This score, ranging from 0 to 1, indicates the likelihood that the images are of the same person, with 0 denoting no similarity and 1 denoting full similarity.

The architecture of Siamese networks consists of two or more identical sub-networks, each having the same configuration, parameters, and weights. In practice, only one of the sub-networks is typically trained, and the same configuration is then applied to the other sub-networks. This approach allows Siamese networks to effectively compare images and determine their similarity, making them particularly useful for tasks such as facial recognition and verification in scenarios with limited training data.

Example)
1. First Subnetwork : The first subnetwork takes an image (A) as input and passes it through convolutional layers and fully connected layers to obtain a vector representation of the image.
2. Second Subnetwork : The second image (B) is passed through a network that is exactly the same as the first one, with the same weights and parameters, to obtain its vector representation.
3. Encoding Comparison : The two encodings, E(A) and E(B), from the respective images are compared to determine how similar the two images are. If the images are similar, the encodings will also be quite similar.
4. Distance Measurement : The distance between the two vectors is measured. If the distance is small, the vectors are considered similar or belonging to the same classes. If the distance is larger, the vectors are considered different from one another.
