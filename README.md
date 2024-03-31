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

* The model is trained using pairs of data.
* For Siamese networks, they operate using pairs of texts, which can either be similar or dissimilar in content. When these text pairs are provided as input to the network, it processes each text independently and compares their features to calculate similarity.
* For example, consider using a Siamese network in a text similarity analysis system. Two different sentences could be provided as input to the network. The network processes each sentence independently and compares their features to determine how similar they are. If the two sentences have the same topic or context, the network will consider them similar; otherwise, it will consider them different.

## Siamese Network

* Siamese networks are well known for one-shot learning, requiring only one training example for each class.
* The key function of these networks is their ability to generate a similarity score between a reference text and a test text. This score ranges from 0 to 1, indicating the likelihood that the two texts have the same topic or context. Here, 0 indicates no similarity, and 1 indicates complete similarity.

![image](https://github.com/inhoi/Siamese-Network/assets/76868046/2871045d-e137-4eaa-a3f0-9078c86b45bc)

The structure of a Siamese network consists of two or more identical sub-networks with the same configuration, parameters, and weights. In practice, usually only one sub-network is trained, and then the same configuration is applied to the other sub-networks. This approach allows Siamese networks to effectively compare texts and determine similarity, making them useful for text classification, similarity analysis, and verification tasks, especially in scenarios with limited training data.

Example)
1. First Subnetwork : The first subnetwork takes an image (A) as input and passes it through convolutional layers and fully connected layers to obtain a vector representation of the image.
2. Second Subnetwork : The second image (B) is passed through a network that is exactly the same as the first one, with the same weights and parameters, to obtain its vector representation.
3. Encoding Comparison : The two encodings, E(A) and E(B), from the respective images are compared to determine how similar the two images are. If the images are similar, the encodings will also be quite similar.
4. Distance Measurement : The distance between the two vectors is measured. If the distance is small, the vectors are considered similar or belonging to the same classes. If the distance is larger, the vectors are considered different from one another.

![image](https://github.com/inhoi/Siamese-Network/assets/76868046/c6b508d7-c5d9-407c-b807-f01dd5d32558)

## Contrastive Loss

![image](https://github.com/inhoi/Siamese-Network/assets/76868046/8c4033f2-5123-421e-b2f6-ef28af82fce1)

* Siamese networks, when applied to text, are used to differentiate between text inputs by learning a distance metric, rather than classifying them into categories.
* They penalize dissimilar text pairs that are too close and similar text pairs that are too far apart in the learned embedding space.

![image](https://github.com/inhoi/Siamese-Network/assets/76868046/95f371e4-5b8f-4bef-88f1-117c9a231d6d)

* Dw is Euclidean distance between the vector representations (embeddings) of text produced by the network.
* Y is a binary indicator with a value of 0 when two text inputs are from the same category (similar) and 1 when they are from different categories (dissimilar).
* max() ifunction is used to choose the greater value between 0 and the difference between the margin, m-dw, effectively applying a zero loss to dissimilar pairs that are sufficiently apart.
* m is a hyperparameter greater than zero. It ensures that dissimilar text pairs that are beyond this margin do not contribute to the loss, providing a buffer zone within the embedding space.

## Triplet Loss

* Allow our model to map two similar texts close and far from dissimilar sample text pairs.
  
![image](https://github.com/inhoi/Siamese-Network/assets/76868046/f69f81f0-0119-4995-9d96-8290be11c458)

1. Anchor — This is a sample text.

2. Positive — This is just another variation of the anchor text. This helps the siamese network model learn the similarities between the two texts.

3. Negative — This is a different text from the above two similar text pairs. This helps our model learn dissimilarities with anchor texts.

![image](https://github.com/inhoi/Siamese-Network/assets/76868046/6e427c22-f688-471c-8266-520f8aab0daf)

* a represents an anchor text.
* p represents a positive text, similar to the anchor.
* n represents a negative text, dissimilar to the anchor.
* d(a,p) denotes the distance between the anchor and the positive text embeddings.
* d(a,n) denotes the distance between the anchor and the negative text embeddings.
* margin is a hyperparameter that specifies how much farther the negative example's embedding should be from the anchor's embedding compared to the positive example's embedding.

