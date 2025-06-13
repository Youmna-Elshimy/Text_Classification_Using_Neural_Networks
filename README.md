# **Text Classification Using Neural Networks**

## **Overview**
This project focuses on building a text classification model to automatically categorize news articles from the BBC dataset into six predefined topics. The goal is to demonstrate how deep learning techniques, especially neural networks with embedding layers, can effectively understand and classify real-world textual data.

## **Data Preprocessing**
The dataset consists of 2,225 news articles labeled by category. To prepare the data:
- Common English stopwords were removed to reduce noise and focus on meaningful words.
- The text was tokenized, turning each article into a sequence of word indices.
- Sequences were padded or truncated to a fixed length of 120 tokens to ensure uniform input size.
- A vocabulary size limit of 1,000 words was set, with rare or unknown words replaced by a special out-of-vocabulary token (<OOV>).
- The dataset was split into 80% training data (1,780 articles) and 20% validation data (445 articles).

## **Model Architecture**
The model is a simple yet effective neural network designed for multi-class classification:
- **Embedding Layer:** Transforms each word index into a 16-dimensional vector representation, allowing the model to capture semantic relationships.
- **Global Average Pooling:** Averages all word embeddings in a sequence into a single vector, reducing variable-length sequences to fixed-size inputs.
- **Dense Layer:** A fully connected hidden layer with 24 neurons and ReLU activation helps the model learn non-linear patterns.
- **Output Layer:** A softmax layer with 6 units, one for each news category, outputs class probabilities.

The model uses the Adam optimizer and sparse categorical cross-entropy loss, appropriate for multi-class classification.

## **Training Process**
The model was trained over 30 epochs on the training set, with performance evaluated on the validation set after each epoch. Key training parameters include:
- **Vocabulary size:** 1000
- **Embedding dimension:** 16
- **Max sequence length:** 120 tokens
- **Padding/truncation:** Applied post-sequence
- **Special token for unknown words:** <OOV>

## **Results and Interpretation**
### **Accuracy**
The training accuracy steadily improved over the epochs, reaching above 99% by the 30th epoch. The validation accuracy also increased rapidly, reaching a peak around 95%, indicating the model effectively learned to generalize from the training data to unseen examples.
The accuracy plot below shows:
- A fast increase in accuracy during the first 10 epochs, reflecting quick learning.
- Validation accuracy closely follows training accuracy with a small gap, indicating limited overfitting.
- Minor fluctuations in validation accuracy towards later epochs are normal and suggest that the model might have reached close to its optimal capacity.

![image](https://github.com/user-attachments/assets/d6b2d7b2-e591-4aa9-b2b7-4c94017a131b)

### **Loss**
The loss plot below reveals:
- Both training and validation loss decrease consistently as the epochs progress.
- Training loss reduces to a very low value (~0.05), showing the model fits the training data well.
- Validation loss stabilizes around ~0.18, confirming good generalization without severe overfitting.

![image](https://github.com/user-attachments/assets/173f9169-40f2-4044-9b92-0eee631b1f84)

### **Overall**
These results demonstrate that the chosen model architecture and preprocessing pipeline effectively classify BBC news articles into their respective categories. The model balances learning from training data while maintaining strong validation performance.
