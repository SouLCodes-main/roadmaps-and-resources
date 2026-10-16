# Machine Learning Roadmap

> A step‑by‑step guide to mastering Machine Learning, from data work and math basics to neural networks and real‑world model deployment.

## Prerequisites

No prior machine learning experience is required,. You should be comfortable with:

- Basic programming concepts such as variables, loops, functions and object‑oriented programming

- General computer science ideas and thinking about algorithms

- High school math like algebra and probability

- Using the command line and Git or GitHub to keep track of code

---

## Learning Path

### 1.. Math Foundations

#### Learn

- [Python for Data Science](https://youtu.be/LHBE6Q9XlzI)

- [Essence of Linear Algebra (3Blue1Brown)](https://youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)

Begin by learning Python, the common language for Machine Learning and the basic math that drives Machine Learning algorithms.

#### Build

Create a **Data Scraper and Statistics Analyzer**. Write a Python script that collects data from a site (such as a weather page or sports statistics) cleans it and computes simple probabilities, averages and standard deviations.

#### You should learn

- Python data structures such as lists, dictionaries and sets

- Functions and object‑oriented programming (OOP)

- Vectors, matrices and dot products

- Basic calculus like derivatives and gradients

- Probability distributions and statistical significance

---

### 2. Data. Visualization

#### Learn

- [Pandas & Data Analysis Tutorial](https://youtu.be/r-uOLxNrNk8)

- [Matplotlib & Seaborn for Data Visualization](https://youtu.be/a9UrKTVEeZA)

Machine Learning models work best when the data is clean. Learn how to tidy arrange and show data clearly. I find this step very important.

#### Build

Conduct an **Exploratory Data Analysis (EDA) Notebook** on the famous [Titanic Dataset](https://www.kaggle.com/c//data).

- Handle missing values and outliers

- Visualize survival rates across demographics

- Extract and engineer new features from existing columns

- Present a clear narrative of your findings

#### You should learn

- NumPy arrays and vectorized operations

- Pandas DataFrames and Series

- Filtering, grouping and aggregating data

- Handling missing or categorical data

- Creating scatter plots, histograms and correlation matrices

---

### 3. Core Machine Learning (Scikit‑Learn)

#### Learn

- [Machine Learning for Everybody](https://youtu.be/i_LwzRmAcko)

- [Scikit‑Learn Crash Course](https://youtu.be/0B5eIE_1vpU)

Move from data analysis to making predictions by using Machine Learning methods on real data. I think this is a transition.

#### Build

Create a **Spam Email Classifier** that uses Natural Language Processing and a classification algorithm.

Your classifier should:

- Convert text emails into features such as TF‑IDF or Count Vectorizer

- Train a model such as Naive Bayes or Logistic Regression

- Evaluate the model using a confusion matrix

- Predict whether new unseen emails are spam or ham

#### You should learn

- Supervised versus unsupervised learning

- Linear and Logistic Regression

- Decision Trees and Random Forests

- Support Vector Machines (SVM)

- K‑Means Clustering

- Model evaluation metrics like Accuracy, Precision, Recall and F1‑Score

- Train‑test splits and cross‑validation

---

### 4. Deep. Neural Networks

#### Learn

- [Neural Networks: Zero to Hero (Andrej Karpathy)](https://youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ)

- [PyTorch for Deep Learning](https://youtu.be/V_xro1bcAuA)

Explore how neural networks work. Learn how they learn internally before using frameworks to build complex models. I find the learning of the internals

#### Build

Create a **Multi‑Layer Perceptron (Neural Network) from Scratch** using standard Python and NumPy.

Your scratch‑built model should:

- Implement matrix multiplications for the forward pass

- Calculate loss

- Write the backpropagation algorithm from the ground up to update weights

- Successfully classify a dataset

*Once complete recreate and expand the model using PyTorch or TensorFlow to classify handwritten digits (MNIST).*

#### You should learn

- Perceptrons and network architecture

- Activation functions such, as ReLU, Sigmoid and Softmax

- Forward propagation and Backpropagation

- Loss. Gradient Descent optimizers (Adam, SGD)

- Convolutional Neural Networks (CNNs) for images

- Framework basics (Tensors, computational graphs)

---

### 5. Model. Mlops Basics

#### Learn

- [FastAPI Tutorial](https://youtu.be/0sOvCWFmrtA)

- [Build and Deploy ML Web Apps with Streamlit](https://youtu.be/VqKqgy81_3U)

A machine learning model is not useful if it stays on your local computer. Learn how to package deploy and share your models with the world.

#### Build

Deploy a *Interactive Image Classification Web App**.

Your app should:

- Allow users to upload an image through a web interface

- Process the image and pass it through a trained Deep Learning model

- Return the predicted class and confidence score in real‑time

- Be deployed live on the web using Streamlit Community Cloud or Hugging Face Spaces

#### You should learn

- Saving and loading models with Pickle, Joblib or framework‑specific savers

- Building REST APIs with FastAPI or Flask

- Creating UIs with Streamlit or Gradio

- Managing environments with requirements.txt and virtual environments

- Basics of containerization using Docker

---

## Projects

### Beginner

- Data Scraper and Statistics Analyzer

- Titanic Survival EDA Notebook

- Basic House Price Predictor (Linear Regression)

### Intermediate

- Spam Email Classifier

- Neural Network Built from Scratch (NumPy only)

- Credit Card Fraud Detection System

### Advanced

- Image Classification Web App deployed via Streamlit

- Custom Object Detection model (using YOLO or Faster R‑CNN)

- End‑to‑End Sentiment Analysis API (FastAPI. Hugging Face Transformers)

- Complete open‑source contribution to a known ML library

---

## Additional Resources

As you progress rely heavily on official documentation and active communities.

- [Scikit‑Learn Documentation](https://scikit-learn.org//user_guide.html)

- [PyTorch Documentation](https://pytorch.org/docs/stable/index.html)

- [TensorFlow Documentation](https://www.tensorflow.org/guide)

- [Kaggle Datasets & Notebooks](https://www.kaggle.com/)

- [Hugging Face Models & Datasets](https://huggingface.co/)

- [StatQuest with Josh Starmer (Concepts)](https://www.youtube.com/c/joshstarmer)

- [Papers with Code (Latest ML Research)](https://paperswithcode.com/)

---

## Completion Checklist

- [ ] Completed the Python & Math Foundations path

- [ ] Built the Data Scraper and Analyzer

- [ ] Completed the Data Manipulation path

- [ ] Built an EDA Notebook

- [ ] Completed the Core Machine Learning path

- [ ] Built the Spam Email Classifier

- [ ] Completed the Deep Learning path

- [ ] Built a Neural Network from scratch

- [ ] Trained a PyTorch/TensorFlow Deep Learning model

- [ ] Completed the Model Deployment path

- [ ] Deployed a ML Web App

- [ ] Built, at least one independent personal ML project

- [ ] Published your code and models on GitHub

---

## Contributing

Found something that could be improved or have a resource to suggest?

See the repository's [CONTRIBUTING.md](../../CONTRIBUTING.md) to learn how to contribute.
