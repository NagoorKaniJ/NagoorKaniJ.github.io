Title: Least square residual Classifier Part - I<!--In the name of Almighty-->
Date: 2017-06-13 18:32
Category: Blog


<!--To display line numbers, use a path-less shebang instead of colons:

    #!python
    print("The path-less shebang syntax *will* show line numbers.")-->


Residual based machine learning algorithms such as Deep Residual Neural Network,
Gradient Boosted Tree are popular and shown great promise in machine learning tasks
like computer vision.

 This is a multi-part series in which I’m planning to cover the following residual based algorithms:

 * **Least square residual classifier basen on singular value decomposition**.
 * [**Least square residual classifier basen on simple deep autoencoders**]({{SITEURL}}content/ONEsalamautoencoders.md).
 * **Least square residual classifier basen on convolutional auto encoders**.


In this post, classification algorithm based on PCA   called **least square residual classifier** is introduced and applied on the MNIST handwritten digit recognition task.


## Description


The problem is given a set of manually classified digits (training set), classify a set of unknown digits (the test set). In this digit recognition task, there are 10 digits $(0~\text{to}~9)$ or $10$ classes to predict.

 We consider each digit in the given set as a vector ${\mathbf{y}} \in \mathbb{R}^n$. The complete space of $\mathbf{y}$ is spanned by a set of $n$ orthonormal basis vectors $\mathcal{U} = \text{span}(\mathbf{u}_1~\cdots~\mathbf{u}_n)$.

 Each digit of specific class $i=0~\cdots~9$ is assumed to attracted to a certain low dimensional subspace $\tilde{\mathcal{U}}_i \subset \mathcal{U}$. Hence all the digits of that specific class say 7 with reasonable accuracy can be approximated while using only the $r$ basis vectors that span $\tilde{\mathcal{U}}_7$.  

 The digit can be approximated by expressing it in terms of these basis vectors by stating:
    $$
    \begin{equation}
    \mathbf{y} =  \mathbf{U}_i~\tilde{\mathbf{y}}_i + \mathbf{r}_i
    \label{expansion}
    \end{equation}
    $$
where $\tilde{\mathbf{y}}_i$ is the coefficient vector, $\mathbf{r}_i =$ residual represents the part of the $\mathbf{y}$ that lies orthogonal to the subspace $\tilde{\mathcal{U}}_i$.

Thus the inner product of $\mathbf{r}_i$ with any of the basis vectors that span $\tilde{\mathcal{U}}_i$ is zero: $\mathbf{U}_i^\top~\mathbf{r}_i = 0$.

The basis vectors of  $\tilde{\mathcal{U}}_i$ are collected in the matrix $\mathbf{U}_i \in \mathbb{R}^{n \times r}$  and $r \ll n$. SVD algorithm identifies the subspace $\tilde{\mathcal{U}}_i$ by computing the singular value decomposition (SVD) of the digit matrix $\mathbf{X}_i$ consisting of all the training digits of one kind, for example 7.

The SVD of $\mathbf{X}_i~i=0~\cdots~9$ is computed by
\begin{equation}
\mathbf{X}_i=\mathbf{U}_i^{\text{full}}~\Sigma_i~\mathbf{W}_i^*
\end{equation}

The orthonormal basis matrix $ \mathbf{U}_{\alpha}$ for optimally approximating $\mathbf{y}$ of class $\alpha$ is given by the first $r$ columns of matrix $\mathbf{U}_{\alpha}^{\text{full}}$.

We should now compute how well known an unknown digit $ \mathbf{y}$ can be represented in the 10 different bases.  This can be done by computing the residual vector in least square problems of type

\begin{equation}
\left\|~\mathbf{y} - \mathbf{U}_i~\tilde{\mathbf{y}}_i~\right\| % \rbrace_2
\label{leastsquare}
\end{equation}

Since each digit is well characterised by the reduced orthogonal basis of its own kind, we expect the norm of the residual vector computed from solving Eq. \ref{leastsquare} using orthogonal basis of the same kind is less than the residual vector computed from solving Eq. \ref{leastsquare} using orthogonal basis of the other classes.

More specifically, for a given unknown digit, if we compute its relative residual in all 10 bases, classify the unknown digit to the class of orthogonal bases with the minimum residual.

-------------------------

-------------------------


## Implementation


Now let us implement the least square residual classifier to classify MNIST digits:

    :::python
    from keras.datasets import mnist
    import numpy as np
    (x_train, y_train), (x_test, y_test) = mnist.load_data()

We now normalize all values between 0 and 1 and we now flatten the $28~\times~28$ images into vectors of size 784.

    :::python
    x_train = x_train.astype('float32') / 255.
    x_test = x_test.astype('float32') / 255.
    x_train = x_train.reshape((len(x_train), np.prod(x_train.shape[1:])))
    x_test = x_test.reshape((len(x_test), np.prod(x_test.shape[1:])))
    x_train = x_train.T
    x_test = x_test.T


we now partition the x_train based on the ten classes and store in a list.


    :::python
    x_train_list = []
    for k in xrange(10):
        components = np.where(y_train == k)[0]
        x_train_list.append(x_train[:, components])

<!--  # print 'salam ', k, x_train[:, components].shape-->


we now create a svd basis for each digit data samples.

    :::python
    U_list = []
    for k in xrange(10):
        U, D, V = np.linalg.svd(x_train_list[k])
        U_list.append(U)


<!--    # print 'salam singular values', U.shape -->

we now select the dominant orthogonal basis and project the training digits on the reduced basis to compute the least square projection error.


    :::python
    mse_train = []
    for r in xrange(40):
        n_train = x_train.shape[1]
        y_train_predict = y_train.copy()
        for i in xrange(0, n_train, 15):
            x = x_train[:, i]
            residual_list = np.ones((10))
            for k in xrange(10):
                U_r = U_list[k][:, :r+1]
                alpha = np.dot(U_r.T, x)
                residual = np.linalg.norm(x - np.dot(U_r, alpha))
                residual_list[k] = residual

            y_train_predict[i] = np.argmin(residual_list)
            mse_train.append(np.mean(np.sqr(y_train - y_train_predict)))


<!--  # print 'salam training error', np.mean(np.sqr(y_train - y_train_predict))-->
  <!--      mse_train.append(np.mean(np.sqr(y_train - y_train_predict)))  -->


we now select the dominant orthogonal basis and project the test digits on the reduced basis to compute the least square projection error.

    :::python <!--  r = 40 -->
    mse_test = []
    for r in xrange(40):
        n_test = x_test.shape[1]
        y_test_predict = y_test.copy()
        for i in xrange(0, n_test, 15):
            x = x_test[:, i]
            residual_list = np.ones((10))
            for k in xrange(10):
                U_r = U_list[k][:, :r+1]
                alpha = np.dot(U_r.T, x)
                residual = np.linalg.norm(x - np.dot(U_r, alpha))
                residual_list[k] = residual

            y_test_predict[i] = np.argmin(residual_list)
            mse_test.append(np.mean(np.sqr(y_test - y_test_predict)))


<!--  # print 'salam test error', np.mean(np.sqr(y_test - y_test_predict)) -->
<!--        mse_test.append(np.mean(np.sqr(y_test - y_test_predict))) -->

We show the mean square error train and test results for the MNIST handwritten digit classification problem as a function of
the number of basis used in the least square residual classifier.

![]({filename}images/ONEsvdclassifierresidual.png){: width=700}

We now show the relative residual norm for all test digit 3 and all test digit 7 in terms of all 10 bases.
We notice in the two figures, that most of the test digits 3 and 7 are best approximated in terms of their own basis.

![]({attach}images/ONEsvdclassifierresiduala.png){: width=700}

We show in the figure below the svd approximation of digit 3 using orthogonal basis  with the different  number of basis vectors 1 to 10. In the top panel, $\mathbf{U}_3$ is used to compute the approximations of test digit 3 with increased basis from left to right and similarly bottom panel use $ \mathbf{U}_5$ to compute the svd approximations of 3.


![]({attach}images/ONEsvdclassifierresidualc.png){: width=700}


We show now how the residual depends on the number of basis vectors. In the left panel, $\mathbf{U}_3$ is used to compute the approximations of test digit 3 and similarly right panel use $\mathbf{U}_5$ to compute the svd approximations of 3.

![]({attach}images/ONEsvdclassifierresidualb.png){: width=700}

We see that the relative residual is considerably smaller in the basis $\mathbf{U}_3$ than in the basis $\mathbf{U}_5$

------------------

Finally, though the least square residual classifier is quite fast in test phase and can be suitable for real time computations, they suffer to classify ugly digits.

---------------------

The layout of this blog is inspired by
[Building Autoencoders in Keras](https://blog.keras.io/building-autoencoders-in-keras.html)

### References



 * [Matrix Methods in Data Mining and Pattern Recognition](http://users.mai.liu.se/larel04/matrix-methods/)
 * [Handwritten digit classification using higher order singular value decomposition](https://pdfs.semanticscholar.org/eda0/95bf52e846e8c560403d485c81e1a932eaeb.pdf)
* [Algorithms in data mining using matrix and tensor    methods](http://liu.diva-portal.org/smash/record.jsf?pid=diva2%3A18011&dswid=9140)
* [Analyses and Test of Handwritten Digit Recognition Algorithm](http://webstaff.itn.liu.se/~bersa48/files/thesisBerkantSavas.pdf)



----------------------
