Download Link: https://assignmentchef.com/product/solved-ece272a-homework-2
<br>
This is the second homework assignment to get you familiar with the machine learning tools. We’re going to deal with another important type of supervised learning: <em>Regression </em>models.

Recall that you did an excellent job analyzing the diabetes data last week. Your boss was happy and he announced an employee party over the weekend.

You’ve received the following invitation:

From: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="02606d71716f636c2c606d71717b426b616b6c612c6f6766">[email protected]</a>

To: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="9ae3f5efdaf3f9f3f4f9b4f7fffe">[email protected]</a>

Subject: Wine tasting competition

To celebrate our current progress and also introduce our diverse company culture, we’re going to hold a wine tasting competition next week! You may not know that drinking is one of my favorite hobbies (surprise!). In fact, I’ve been a certified sommelier since I joined the company in 1990, and I’ve collected a lot of information about different wines over the years.

For the competition, I would like you to recommend the most tasting wine out of a dozens of options to me. If you pick the one with high quality, you can have an extra week of paid vacation!

I know most of you are more professional being a data analyst than a sommelier, so I would like to provide enough wine data for you to leverage your expertise!

Different from the diabetes outcome, the wine quality is scored from 0 to 10, instead of being labeled as good or bad. <strong>You can either use </strong><em>Regression </em><strong>techniques to predict a real number, or still use </strong><em>classification </em><strong>methods to predict multiple categories</strong>. A lot of classifiers you’ve used also have variants for regression tasks. This should be an interesting off-work activity for you!

<h1>1           Dataset</h1>

<strong>Ensure you’ve download the latest version of the data set from Piazza</strong>

We are using data from the <em>White Wine Quality Data Set</em>, a data set related to white variants of the Portuguese ”Vinho Verde” wine. For more details, consult: <a href="https://www.vinhoverde.pt/en/about-vinho-verde">https://www.vinhoverde.pt/en/about-vinho-verde</a> or [1].

Due to privacy and logistic issues, the features are physicochemical stats and qualities are sensory variables from three wine experts (e.g. there is no data about grape types, wine brand, wine selling price, etc.). Each expert graded the wine quality between 0 (very bad) and 10 (very excellent).

The file is provided in a format known as Comma Separated Values (CSV). You can open it as raw text to take a look! The data columns have 11 variables on quantifying the chemical properties of each wine: fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, and alcohol. All of these fields come in floating point numbers. This data set doesn’t have any missing values.

Quality is the one you want to predict! It is a categorical variable ranged from 0 to 10, where 0 indicates poor quality and 10 indicates high quality.

You can use any method to load in the csv files. Refer to the <em>Getting Started </em>guide if you are not sure about this step.

<h1>2           Recommended Flow</h1>

The flow is similar to homework 1, but with different objectives. You can reuse the data loading and preprocessing functions from the last assignment.

<h1>3           Problem Formulation</h1>

<table width="493">

 <tbody>

  <tr>

   <td colspan="3" width="126"><strong>Input</strong></td>

   <td width="88"><strong>Range</strong></td>

   <td colspan="2" width="279"><strong>Description</strong></td>

  </tr>

  <tr>

   <td colspan="3" width="126">fixed acidity</td>

   <td width="88">[3.8,14.2]</td>

   <td colspan="2" width="279">Various types of acids found in grapes</td>

  </tr>

  <tr>

   <td colspan="3" width="126">volatile acidity</td>

   <td width="88">[0.08,1.1]</td>

   <td colspan="2" width="279">Acids that are distilled out</td>

  </tr>

  <tr>

   <td colspan="3" width="126">citric acid</td>

   <td width="88">[0.0,1.66]</td>

   <td colspan="2" width="279">One of the fixed acids which gives freshness</td>

  </tr>

  <tr>

   <td colspan="3" width="126">residual sugar</td>

   <td width="88">[0.6,65.8]</td>

   <td colspan="2" width="279">Natural sugar from grapes after fermentation</td>

  </tr>

  <tr>

   <td colspan="3" width="126">chlorides</td>

   <td width="88">[0.009,0.346]</td>

   <td colspan="2" width="279">Major contributor to saltiness</td>

  </tr>

  <tr>

   <td colspan="3" width="126">free sulfur dioxide</td>

   <td width="88">[2.0,289.0]</td>

   <td colspan="2" width="279">Amount of the <em>SO</em><sub>2 </sub>that is not bound</td>

  </tr>

  <tr>

   <td colspan="3" width="126">total sulfur dioxide</td>

   <td width="88">[9.0,440.0)</td>

   <td colspan="2" width="279">Sum total of the bound and the free <em>SO</em><sub>2</sub></td>

  </tr>

  <tr>

   <td colspan="3" width="126">density</td>

   <td width="88">[0.99,1.04]</td>

   <td colspan="2" width="279">Mass of wine per unit volume</td>

  </tr>

  <tr>

   <td colspan="3" width="126">pH</td>

   <td width="88">[2.72,3.82]</td>

   <td colspan="2" width="279">A value to specify the acidity/basicity</td>

  </tr>

  <tr>

   <td colspan="3" width="126">sulphates</td>

   <td width="88">[0.22,1.08]</td>

   <td colspan="2" width="279">Mineral salts connected to fermentation</td>

  </tr>

  <tr>

   <td colspan="3" width="126">alcohol</td>

   <td width="88">[8.0,14.2]</td>

   <td colspan="2" width="279">% vol or alcohol by volume (ABV)</td>

  </tr>

  <tr>

   <td width="65"><strong>Output</strong></td>

   <td width="58"><strong>Range</strong></td>

   <td colspan="3" width="357"><strong>Description</strong></td>

   <td width="14"> </td>

  </tr>

  <tr>

   <td width="65">quality</td>

   <td width="58">[3,9]</td>

   <td colspan="3" width="357">Wine quality between 0 (very bad) and 10 (very excellent)</td>

   <td width="14"> </td>

  </tr>

  <tr>

   <td width="65"></td>

   <td width="58"></td>

   <td width="4"></td>

   <td width="92"></td>

   <td width="261"></td>

   <td width="13"></td>

  </tr>

 </tbody>

</table>

Your task is to create a classifier that converts physicochemical data of the white wines into a prediction for how good is the quality of the wine.

You are required to use the Python scikit-learn library to construct your models. You are required to use the following eight methods:

<ul>

 <li><strong>Logistic Regression</strong></li>

 <li><strong>Linear Regression</strong></li>

 <li><strong>Multi Layer Perceptrons Classifier (MLPC)</strong></li>

 <li><strong>Multi Layer Perceptrons Regressor (MLPR)</strong></li>

 <li><strong>Support Vector Classification (SVC)</strong></li>

 <li><strong>Support Vector Regression (SVR)</strong></li>

 <li><strong>Gaussian Process Classifier (GPC)</strong></li>

 <li><strong>Gaussian Process Regressor (GPR)</strong></li>

</ul>

However, you can experiment any other algorithms you find interesting! Links to the documentation for more methods is available on <a href="https://scikit-learn.org/stable/supervised_learning.html"><strong>Supervised </strong></a><a href="https://scikit-learn.org/stable/supervised_learning.html"><strong>Learning in SciKit Learn</strong></a><a href="https://scikit-learn.org/stable/supervised_learning.html">)</a>

After you have trained your algorithms and selected the one you think is best, train it on the whole training set, then predict on the data in <em>unknowns.csv</em>. Make a new CSV file, <em>scores.csv</em>, with only one column, the predicted wine quality, and submit it with your report.

You also must write a brief report answering the following questions:

<ol>

 <li><strong>Show the distribution of the quality variable </strong>(Hint: use histogram). How many samples are in each category? Is this a balanced data set?</li>

 <li><strong>Compute the correlation matrix between any two features</strong>. What correlations do you observe?</li>

 <li><strong>How regression methods are different from the classification methods in terms of their prediction results?</strong></li>

 <li>The following questions are intended to test your understanding of themodels listed above: (Hint: Answers can be found in lecture slides and/or <a href="https://scikit-learn.org/stable/supervised_learning.html">SciKit Learn website.</a>)

  <ul>

   <li>Mathematically Linear Regression solves a problem of the form:</li>

  </ul></li>

</ol>

Explain the above formula, what does <em>X</em>, <em>w</em>, and <em>y </em>represent respectively?

<ul>

 <li>Logistic regression, despite its name, is a linear model for classification. Compared to the Linear Regression, it applies a so called logistic function (or sigmoid function) to the hypothesis. Explain what is a logistic function?</li>

 <li>What is the difference between a Multi-layer Perceptron Classifierwith logistic activation function and a Logistic Regressor?</li>

 <li>What is the activation function used in Multi-layer Perceptron Regressor? Can we use sigmoid as its activation function, if not, why?</li>

 <li>The output of SVC’s decision function for a given sample <em>x </em>can be written as:</li>

</ul>

X

<em>y<sub>i</sub>α<sub>i</sub>K</em>(<em>x<sub>i</sub>,x</em>) + <em>b </em><em>i</em>∈<em>SV</em>

Explain the above decision function, what does <em>α </em>and <em>K </em>represent respectively?

<ul>

 <li>Give two linearly separable classes, the objective of SVM is to finda hyperplane that separates these two classes with minimum error while also maximizes the the perpendicular distance between the two closes points from either of these two classes. Explain how SVM can be used for regression? (Hint: SVR introduces a slack variable )</li>

 <li>Why Gaussian Process has slow performance for larger datasets (Hint: look into the kernel function for GP)?</li>

 <li>How is Gaussian Process fundamentally different from the abovemodels?</li>

</ul>

<ol start="5">

 <li>Evaluate your choices of model with cross-validation (CV). What is theCV accuracy on training data and validation data for each model? <strong>Use a table or scatter plot to show the accuracy results. </strong>Which one has the best performance? Do you observe overfitting/underfitting?</li>

</ol>