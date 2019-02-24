**Loss Function**

Evaluates how well specific algorithm models the given data. If predictions
deviate too much from actual results, loss function would cough up a very large
number. Gradually, with the help of some optimization function, loss function
learns to reduce the error in prediction.

There are various factors involved in choosing a loss function for specific
problem such as type of machine learning algorithm chosen, ease of calculating
the derivatives and to some degree the percentage of outliers in the data set.

Broadly, loss functions can be classified into two major categories depending
upon the type of learning task we are dealing with — Regression losses and
Classification losses :

-   In classification, we are trying to predict output from set of finite
    categorical values.

-   Regression, on the other hand, deals with predicting a continuous value.

n – Number of training examples

i – ith training example in a data set

![equation](http://latex.codecogs.com/gif.latex?$$y_{i}$$) – truth label for ith training example

![equation](http://latex.codecogs.com/gif.latex?$${\hat{y}}_{i}$$) – Prediction for ith training example.

! Regression functions predict a quantity, and classification functions predict
a label.

*Regression losses :* Mean Bias Error, Mean Squared Error, Mean Absolute Error,
Mean Absolute Percentage Error, Mean squared logarithmic error, Huber Loss /
Smooth Mean Absolute Error, Log cosh Loss, Poisson Loss.

*Classification losses :* Categorical Crossentropy, Binary crossentropy, Log
Loss, Focal Loss, Kullback (KL) Divergence / Relative Entropy, Exponential Loss,
Squared Hinge Loss, Hinge Loss

**Regression Losses**

*L1 Loss function*

Stands for Least Absolute Deviations. Also known as LAD.

![equation](http://latex.codecogs.com/gif.latex?$$&space;L1LossFunction&space;=&space;\&space;\sum_{i&space;=&space;1}^{n}\left|&space;y_{i}&space;-&space;\&space;\hat{y_{i}}&space;\right|&space;$$)

*L2 Loss function*

stands for Least Square Errors. Also known as LS.

![equation](http://latex.codecogs.com/gif.latex?$$&space;L2LossFunction&space;=&space;\&space;\sum_{i&space;=&space;1}^{n}\left|&space;y_{i}&space;-&space;\&space;\hat{y_{i}}&space;\right|&space;$$)

Generally, L2 Loss Function is preferred in most of the cases. But when the
outliers are present in the dataset, then the L2 Loss Function does not perform
well. The reason behind this bad performance is that if the dataset is having
outliers, then because of the consideration of the squared differences, it leads
to the much larger error. Hence, L2 Loss Function is not useful here. Prefer L1
Loss Function as it is not affected by the outliers or remove the outliers and
then use L2 Loss Function.

*Mean Bias Error*

![equation](http://latex.codecogs.com/gif.latex?$$&space;MBE&space;=&space;\&space;\frac{\sum_{i&space;=&space;1}^{n}{{(y}_{i}&space;-&space;\&space;\hat{y_{i}})}}{n}&space;$$)

Clearly there’s a need for caution as positive and negative errors could cancel
each other out.

*Mean Absolute Error / L1 Loss*

![equation](http://latex.codecogs.com/gif.latex?$$&space;MAE&space;=&space;\&space;\frac{\sum_{i&space;=&space;1}^{n}\left|&space;y_{i}&space;-&space;\&space;\hat{y_{i}}&space;\right|}{n}&space;$$)

Mean absolute error is measured as the average of sum of absolute differences
between predictions and actual observations. MAE loss is useful if the training
data is corrupted with outliers.

![https://cdn-images-1.medium.com/max/1000/1\*8BQhdKu1nk-tAAbOR17qGg.png](img/lf_01.png)

*Mean Squared Error / Quadratic Loss / L2 Loss*

![equation](http://latex.codecogs.com/gif.latex?$$&space;MSE&space;=&space;\&space;\frac{\sum_{i&space;=&space;1}^{n}{(y_{i}&space;-&space;\&space;\hat{y_{i}})}^{2}}{n}&space;$$)

Mean square error is measured as the average of squared difference between
predictions and actual observations. The most commonly used regression loss
function.

![https://cdn-images-1.medium.com/max/1000/1\*EqTaoCB1NmJnsRYEezSACA.png](img/lf_02.png)

! In short, using the squared error is easier to solve, but using the absolute
error is more robust to outliers.

*Mean absolute percentage error*

![equation](http://latex.codecogs.com/gif.latex?$$&space;MAPE&space;=&space;\&space;\frac{1}{n}*\sum_{i&space;=&space;1}^{n}\frac{\left|&space;y_{i}&space;-&space;\&space;\hat{y_{i}}&space;\right|}{max(\left|&space;y_{i}&space;\right|,\&space;\epsilon)}*100&space;$$)

*Mean squared logarithmic error*

<img src="http://latex.codecogs.com/gif.latex?$$MSLE&space;=&space;\&space;\frac{1}{n}*\sum_{i&space;=&space;1}^{n}{((log(y_{i}}{&plus;&space;1)&space;-&space;\&space;log({\hat{y}}_{i}&space;&plus;&space;1))}^{2}&space;$$" title="$$MSLE = \ \frac{1}{n}*\sum_{i = 1}^{n}{((log(y_{i}}{+ 1) - \ log({\hat{y}}_{i} + 1))}^{2} $$" />

*Log cosh*

![equation](http://latex.codecogs.com/gif.latex?$$&space;{Log\&space;cosh}&space;=&space;\&space;\frac{1}{n}*\sum_{i&space;=&space;1}^{n}{log(cosh(}{\hat{y}}_{i}&space;-&space;\&space;y_{i}))&space;$$)

![equation](http://latex.codecogs.com/gif.latex?$$&space;\cosh\left(&space;t&space;\right)&space;=&space;\frac{\exp\left(&space;t&space;\right)&space;&plus;&space;exp(&space;-&space;t)}{2}&space;$$)

![https://cdn-images-1.medium.com/max/1000/1\*BAbgW_JdwyAWLZR2dE1Ujg.png](img/lf_03.png)

Advantage : works mostly like the mean squared error, but will not be so
strongly affected by the occasional wildly incorrect prediction. It has all the
advantages of Huber loss, but unlike Huber loss it’s twice differentiable
everywhere (For ML frameworks like XGBoost, twice differentiable functions are
more favourable).

*Huber Loss / Smooth Mean Absolute Error*

<img src="http://latex.codecogs.com/gif.latex?$$&space;L_{\delta}&space;=&space;\left\{&space;\begin{matrix}&space;\frac{1}{2}*(y_{i}&space;-&space;{{\hat{y}}_{i})}^{2}\text{\&space;\&space;\&space;for\&space;}\left|&space;y_{i}&space;-&space;{\hat{y}}_{i}&space;\right|&space;\leq&space;\delta&space;\\&space;\delta\left|&space;y_{i}&space;-&space;{\hat{y}}_{i}&space;\right|&space;-&space;\frac{1}{2}\delta^{2}\text{\&space;\&space;\&space;otherwise}&space;\\&space;\end{matrix}&space;\right.\&space;$$" title="$$ L_{\delta} = \left\{ \begin{matrix} \frac{1}{2}*(y_{i} - {{\hat{y}}_{i})}^{2}\text{\ \ \ for\ }\left| y_{i} - {\hat{y}}_{i} \right| \leq \delta \\ \delta\left| y_{i} - {\hat{y}}_{i} \right| - \frac{1}{2}\delta^{2}\text{\ \ \ otherwise} \\ \end{matrix} \right.\ $$" />

Huber loss is less sensitive to outliers in data than the squared error loss.
It’s also differentiable at 0. It’s basically absolute error, which becomes
quadratic when error is small. How small that error has to be to make it
quadratic depends on a hyperparameter, 𝛿 (delta), which can be tuned. Huber loss
approaches MAE when 𝛿 \~ 0 and MSE when 𝛿 \~ ∞ (large numbers.)

![https://cdn-images-1.medium.com/max/1000/1\*jxidxadWSMLvwLDZz2mycg.png](img/lf_04.png)

The choice of delta is critical because it determines what you’re willing to
consider as an outlier. Residuals larger than delta are minimized with L1 (which
is less sensitive to large outliers), while residuals smaller than delta are
minimized “appropriately” with L2.

*Poisson*

Poisson loss function is a measure of how the predicted distribution diverges
from the expected distribution.

![equation](http://latex.codecogs.com/gif.latex?$$&space;L&space;=&space;\frac{1}{n}\sum_{i&space;=&space;1}^{n}{({\hat{y}}_{i}&space;-&space;y_{i}*\log\left(&space;{\hat{y}}_{i}&space;\right))}&space;$$)

**Classification Losses**

*Hinge Loss / Multi class SVM Loss*

The hinge loss is used for “maximum-margin” classification, most notably for
support vector machines (SVMs).

![equation](http://latex.codecogs.com/gif.latex?$$&space;SVMLoss&space;=&space;\&space;\frac{1}{n}\sum_{i&space;=&space;1}^{n}{max(1&space;-&space;{\hat{y}}_{i}*y_{i},0)}&space;$$)

*Squared Hinge Loss / Squared Multi class SVM Loss*

![equation](http://latex.codecogs.com/gif.latex?$$y_{i}$$) 𝛜 {-1,1}

![equation](http://latex.codecogs.com/gif.latex?$$&space;SVMLossSquared&space;=&space;\&space;\frac{1}{n}\sum_{i&space;=&space;1}^{n}{(max(1&space;-&space;{\hat{y}}_{i}*y_{i},0))^{2}}&space;$$)

*Cross Entropy Loss / Negative Log Likelihood / Binary Cross Entropy*

This is the most common setting for classification problems. Cross-entropy loss
increases as the predicted probability diverges from the actual label.

![equation](http://latex.codecogs.com/gif.latex?$$&space;CrossEntropyLoss&space;=&space;\&space;-&space;\frac{1}{n}\sum_{i&space;=&space;1}^{n}{\lbrack&space;y_{i}\log\left(&space;{\hat{y}}_{i}&space;\right)&space;&plus;&space;\left(&space;1&space;-&space;y_{i}&space;\right)\log\left(&space;1&space;-&space;{\hat{y}}_{i}&space;\right)\rbrack}&space;$$)

In short, we are just multiplying the log of the actual predicted probability
for the ground truth class.

*Kullback (KL) Divergence / Relative Entropy*

KL Divergence, also known as relative entropy, information divergence/gain, is a
measure of how one probability distribution diverges from a second expected
probability distribution.

![equation](http://latex.codecogs.com/gif.latex?$$&space;L&space;=&space;\&space;\frac{1}{n}\sum_{i&space;=&space;1}^{n}{\lbrack&space;y_{i}&space;-&space;log(\frac{y_{i}}{{\hat{y}}_{i}})\rbrack}&space;=&space;\frac{1}{n}\sum_{i&space;=&space;1}^{n}{\left(&space;y_{i}*\log\left(&space;y_{i}&space;\right)&space;\right)&space;-&space;\frac{1}{n}\sum_{i&space;=&space;1}^{n}{(y_{i}*\log\left(&space;{\hat{y}}_{i}&space;\right))}}&space;$$)

References :

<https://towardsdatascience.com/common-loss-functions-in-machine-learning-46af0ffc4d23>

<https://heartbeat.fritz.ai/5-regression-loss-functions-all-machine-learners-should-know-4fb140e9d4b0>

<https://isaacchanghau.github.io/post/loss_functions/>
