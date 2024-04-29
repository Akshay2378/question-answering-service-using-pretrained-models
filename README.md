# question-answering-service-using-pretrained-models
We'll use Keras to define the architecture. Our model consists of input sequences and questions, both treated as Keras Input layers. These sequences are then encoded using Embedding layers to capture their semantic meaning. To facilitate the matching between input sequences and questions, we implement a mechanism that compares their vectors. This forms the core of our memory network architecture.


Once the architecture is defined, we compile the model using the 'rmsprop' optimizer and 'categorical_crossentropy' loss function. This step prepares the model for training by specifying how it should update its parameters to minimize the loss during training.

With the model compiled, we move on to training. We use the model.fit() function in Keras to train the model on our training data, which includes input sequences, corresponding questions, and their respective answers. During training, we employ a custom TrainingVisualizer callback to monitor and visualize training metrics such as loss and accuracy.

After training, it's time to evaluate the model's performance. We do this by testing it on a separate dataset consisting of input sequences, questions, and expected answers. We then analyze the model's predictions against the ground truth answers. In this video, we'll print the test results for the first 10 test samples to demonstrate how well our model performs.
Imports and Reading Data
The code starts by importing necessary libraries:
NumPy for numerical operations.
pandas for data manipulation.
os for interacting with the operating system.
It reads three text files (q1.txt, q2.txt, q3.txt) into pandas DataFrames:
df_08, df_09, df_10 are created using pd.read_csv() to load the text files.
These DataFrames likely contain questions and answers from different years.
Data Cleaning
Columns 'Question' and 'Answer' are selected from df_08, df_09, and df_10 and concatenated into df_all using pd.concat().
To clean the data:
Rows with missing values are dropped using dropna().
Duplicate questions are removed to create df_all_2.
Approximate Matching Function
The getApproximateAnswer(q) function is defined.
It uses the Levenshtein ratio from the Levenshtein package to find the closest matching question in df_all_2 to the input question q.
This function helps find answers to questions even if they are not exact matches to what's in the dataset.
Model Building
An end-to-end memory network for question answering is built using Keras.
The model components:
Input sequences and questions are defined as Keras Input layers.
Input sequences are encoded using Embedding layers.
A matching mechanism is applied between input and question vectors.
The model is compiled using the 'rmsprop' optimizer and 'categorical_crossentropy' loss.
Training the Model
The model is trained using model.fit() with the training data:
inputs_train, queries_train, answers_train.
This is where the model learns to predict answers based on input sequences and questions.
A custom TrainingVisualizer callback is used to visualize training metrics.
This callback likely helps monitor the model's performance during training.
Testing and Evaluation
The model is evaluated on the test data:
inputs_test, queries_test, answers_test.
Test results for the first 10 test samples are printed.
This gives an idea of how well the model performs on unseen data.
Conclusion
Overall, this code snippet demonstrates a pipeline for building, training, and evaluating a question-answering model:
Data is imported, cleaned, and preprocessed.
An approximate matching function helps handle variations in input questions.
A memory network model is built in Keras for question answering.
The model is trained and evaluated, with results printed for assessment.
This entire process aims to create a system that can understand and answer questions based on a given dataset, even when questions are not exact matches. It's a simplified version of a question-answering system, often used in chatbots, customer support systems, or information retrieval applications.
