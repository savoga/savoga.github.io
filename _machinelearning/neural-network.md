---
layout: maths
name: Neural network
category: Supervised learning
---

**Neural network (one layer)**

<ins>Logistic regression with a neural network mindset</ins>

Let us take the example of an image that we want to classify in a
**binary** way: man/woman

The picture is vectorized as a vector of pixels :
$$\begin{pmatrix}x_1 \\
    \vdots \\
    x_p
\end{pmatrix}$$

We use a regression to predict if it's a man/woman: $y=\omega^Tx + b$

Note: $x$ are all the pixels of **one** image.

We want a probability in output (if it's $\ge 0.5$ then we say it's a
man).

We thus want the output to be
$\widehat{y}=\sigma(\omega^Tx + b)=\mathbb{P}(y|x) \in [0,1]$

(see regression part to get more details on the sigmoid)

Now since it's a binary classification, we want the $y$ (real value) to
be $0$ or $1$.

Thus, the loss function is:

$$\mathcal{L}(y, \widehat{y})=-y\log(\widehat{y})+(1-y)\log(1-\widehat{y})$$

The cost function is the empiric loss on all examples:

$$J(\omega, b)=\frac{1}{m}\Sigma_{i=1}^m\mathcal{L}(\widehat{y}^{(i)}, y^i)$$

<ins>Forward propagation</ins>

$$x_1,x_2, \omega_1,\omega_p,b \to z=\omega_1x_1 + \omega_2x_2 + b \to \widehat{y}=a=\sigma(z) \to \mathcal{L}(a,y)$$

\- First arrow: regression

\- Second arrow: probability

\- Third arrow: error

<ins>Backward propagation</ins>

The idea is: with the error computed on the last step, we go backward in
order to correct the parameters $\omega$ and $b$.

$$x_1,x_2, \omega_1,\omega_p,b \leftarrow z=\omega_1x_1 + \omega_2x_2 + b \leftarrow \widehat{y}=a=\sigma(z) \leftarrow \mathcal{L}(a,y)$$

To find the new value of $\omega_1$ we look for its change ($d \omega_1$) that we can obtain thanks to the **Chain rule**. It consists of decomposing the derivative into successive ones:

$\frac{d\mathcal{L}}{d\omega_1}="d\omega_1"=\frac{d\mathcal{L}}{da}\frac{da}{dz}\frac{dz}{d\omega_1}=...=(a-y)x_1=dzx_1$ (details on the derivatives can be found <a class="cleanLinkSource" href="https://www.youtube.com/watch?v=z_xiwjEdAC4">here</a>)

*Note*: we can see that the updated weight depends on the previous prevision $a$. This is why it is necessary to recompute the predicted value at each iteration.


    for i in range(num_iterations):
            
         # Cost and gradient calculation
         grads, cost = propagate(w, b, X_train, Y_train) # propagation on ALL the training sample
            
         # Retrieve derivatives from grads
         dw = grads["dw"]
         db = grads["db"]
            
         # update parameters
         w = w - learning_rate * dw
         b = b - learning_rate * db
            
         # Record the costs
         costs.append(cost)

    def propagate(w, b, X, Y):
        
        m = X.shape[1]
        
        # FORWARD PROPAGATION (FROM X TO COST)
        A = sigmoid(np.dot(w.T,X)+b)
        cost = (- 1 / m) * np.sum(Y * np.log(A) + (1 - Y) * (np.log(1 - A))
        
        # BACKWARD PROPAGATION (TO FIND GRAD)
        dw = (1/m)*np.dot(X,(A-Y).T)
        db = (1/m)*np.sum(A-Y)
