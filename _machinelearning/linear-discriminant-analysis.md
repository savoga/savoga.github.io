---
layout: maths
name: Linear discriminant analysis
category: Supervised learning
---

**Linear discriminant analysis**

We focus on the binary case, that is when $Y=+1$ or $Y=-1$, that is to
sets of variables.

These two conditional laws need to be gaussians with same covariance:

$X \| Y=+1 \sim \mathcal{N}(\mu_+,\Sigma)$ with density $f_+$

$X \| Y=-1 \sim \mathcal{N}(\mu_-,\Sigma)$ with density $f_-$

Let $\pi_+$, $\pi_-$ be the simple probabilities $P(Y=+1)$, $P(Y=-1)$

$\mathbb{P}(Y=+1 \| X=x) = \frac{\mathbb{P}(Y=+1, X=x)}{\mathbb{P}(X=x)}$

$\mathbb{P}(Y=+1 \| X=x) = \frac{\mathbb{P}(X=x \| Y=+1) \mathbb{P}(Y=+1) }{\mathbb{P}(X=x) }$

$\mathbb{P}(Y=+1 \| X=x) = \frac{f_+ \pi_+}{\mathbb{P}(X=x) }$

$\mathbb{P}(Y=+1 \| X=x) = \frac{f_+ \pi_+}{\mathbb{P}(X=x \| Y=+1)\mathbb{P}(Y= +1) + \mathbb{P}(X=x \| Y=-1)\mathbb{P}(Y= -1) }$

$\mathbb{P}(Y=+1 \| X=x) = \frac{f_+ \pi_+}{(f_+\pi_+ + f_-\pi_-)}$

Similarly,

$\mathbb{P}(Y=-1 \| X=x) = \frac{f_- (1-\pi_+)}{\mathbb{P}(X=x) }$

$\mathbb{P}(Y=-1 \| X=x) = \frac{f_- (1-\pi_+)}{(f_+\pi_+ + f_-\pi_-)}$

The result shows us that we can express the two conditionnal
probabilities in terms of conditionnal densities and \"simple\"
probabilities ($\pi_+$, $\pi_-$).

Recall that multivariable gaussian density is:
$f(x)=\frac{1}{\sqrt{2 \pi |\Sigma|}}e^{-\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x-\mu)}$

In practice, $\mu_+$, $\mu_-$, $\pi_+$ and $\Sigma$ are unknown. Thus we
use empiric values:

$$\widehat{\pi}_+ = m/n$$

$$\widehat{\mu}_+ = \frac{1}{m} \Sigma 1_{\{y_i=+1\}}x_i$$

$$\widehat{\mu}_- = \frac{1}{n-m} \Sigma 1_{\{y_i=-1\}}x_i$$

$$\widehat{\Sigma} = \frac{1}{n-2} ((m-1) \widehat{\Sigma}_+ + (n-m-1)\widehat{\Sigma}_-)$$

$$\widehat{\Sigma}_+ = \frac{1}{m-1} \Sigma 1_{\{y_i=+1\}}(x_i-\widehat{\mu}_+)(x_i-\widehat{\mu}_+)^T$$

$$\widehat{\Sigma}_- = \frac{1}{n-m-1} \Sigma 1_{\{y_i=-1\}}(x_i-\widehat{\mu}_-)(x_i-\widehat{\mu}_-)^T$$

<ins>Classification</ins>

We predict class = 1 when $\mathbb{P}(Y=+1 \| X) > \mathbb{P}(Y=-1 \| X)$

=\> $\frac{\mathbb{P}(Y=+1 \| X)}{\mathbb{P}(Y=-1 \| X)} > 1$

=\> $\log(\frac{\mathbb{P}(Y=+1 \| X)}{\mathbb{P}(Y=-1 \| X)}) > 0$

Using previous conditional probability expressions, we end up with the
following prediction rule:

$$\begin{cases}
      1 & \text{if}\ x^T\widehat{\Sigma}^{-1}(\widehat{\mu}_+ - \widehat{\mu}_-) > \frac{1}{2}\widehat{\mu}_+^T\widehat{\Sigma}\widehat{\mu}_+ - \frac{1}{2}\widehat{\mu}_-^T\widehat{\Sigma}\widehat{\mu}_- + \log(1-m/n) - \log(m/n) \\
      -1 & \text{otherwise}
    \end{cases}$$

$$\widehat{\mu}_{+}$$
, $$\widehat{\mu}_-$$,
 $$\widehat{\pi}_+$$ and
$$\widehat{\Sigma}$$ will be computed with *train data*.

$x$ is the *test data*.

*Note*: $$\widehat{\Sigma}^{-1}(\widehat{\mu}_+ - \widehat{\mu}_-)$$ is
the **Fisher function** (see Saporta document).


    class LDAClassifier():
        
        def fit(self, X, y):       
            
            X_p = X[y == 1, :]
            X_m = X[y == -1, :]
            
            X_p_x1 = X_p[:,0]
            X_p_x2 = X_p[:,1]
            X_m_x1 = X_m[:,0]
            X_m_x2 = X_m[:,1]
            
            n = len(X)
            m = len(X_p)
            
            mean_p_x1 = np.mean(X_p_x1)
            mean_p_x2 = np.mean(X_p_x2)
            mean_p = np.array([mean_p_x1,mean_p_x2]) # mu_plus (estimated)
            cov_p = np.cov(np.transpose(X_p))
            

            mean_m_x1 = np.mean(X_m_x1)
            mean_m_x2 = np.mean(X_m_x2)
            mean_m = np.array([mean_m_x1,mean_m_x2]) # mu_minus (estimated)
            cov_m = np.cov(np.transpose(X_m))
            
            cov_est = (1/(n-2))*( (m-1)* cov_p + (n-m-1)* cov_m) # sigma (estimated)
            inv_cov_est = np.linalg.inv(cov_est)
            
            a1 = np.dot(np.transpose(mean_p),inv_cov_est)
            a2 = np.dot(np.transpose(mean_m),inv_cov_est)
            
            # 2nd term in inequality
            self.alpha = 0.5*(np.dot(a1,mean_p)  - 0.5*np.dot(a2,mean_m)) + np.log(1- m/n) - np.log(m/n)
            # 1st term in inequality
            self.beta =  np.dot(inv_cov_est,mean_p-mean_m)
            
            return self
        
        def predict(self, X):
            
            y_=[]
            
            for i in range(len(X)):
                X_pred = X[i]
                beta = np.dot(np.transpose(X_pred), self.beta)
                if (beta>self.alpha):
                    Y_pred = 1
                else:
                    Y_pred = -1
                y_.append(Y_pred)
            return np.array(y_) 
