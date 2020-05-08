On note
$\hat \theta = {\rm arg} \displaystyle\min_{\theta} \frac{1}{2}\| \mathbf{y} -X \theta \|_2^2+ \frac{\lambda}{2}\|\theta\|_2^2$
l'estimateur Ridge

Soit
$f: \theta \mapsto \frac{1}{2}||Y-X\theta||_2^2+\frac{\lambda}{2}||\theta||_2^2$\
1) Quand $X=Id_n$ on a $n=p+1$ et
$f(\theta)=\frac{1}{2}||Y-Id_n\theta||_2^2+\frac{\lambda}{2}||\theta||_2^2$\
Pour des questions de notations, on utilisera $Id_n=Id_{p+1}=Id$\
$f(\theta)=\frac{1}{2}\Sigma_{i=1}^n(Y_i-Id_i\theta)^2+\frac{\lambda}{2} \Sigma_{i=1}^n \theta_i^2$\
Le minimum de la fonction est atteint lorsque $\nabla f(\theta) = 0$\
$\nabla f(\theta) = 0 => \forall k=1,...,p: \frac{\partial f(\theta)}{\partial \theta_k}=0$\
$\frac{\partial f(\theta)}{\partial \theta_k}=2\frac{1}{2} (-Id_{i,k}) \Sigma_{i=1}^n (Y_i-\Sigma_{j=1}^pId_{i,j}\theta_j)+2\frac{\lambda}{2} \theta_k$\
$~~~~~~~=-\Sigma_{i=1}^n(Id_{i,k}Y_i-Id_{i,k}Id_i\theta)+\lambda \theta_k$\
Donc
$\nabla f(\theta)=-\Sigma_{i=1}^n(Id_i^TY_i-Id_i^TId_i\theta)+\lambda \theta=-\Sigma_{i=1}^nId_i^TY_i+\Sigma_{i=1}^nId_i^TId_i \theta +\lambda \theta$\
$~~~~~~~~~~~~~~~~~=-Y+\theta+\lambda \theta$\
$\nabla f(\theta) = 0 => \theta = \frac{1}{1+\lambda}Y= \hat{\theta}_{n,\lambda}^{Ridge}$\
2) Pour $X \in \mathbb{R}^{n \times p}$ quelconque,
$f(\theta)=\frac{1}{2}\Sigma_{i=1}^n(Y_i-X_i\theta)^2+\frac{\lambda}{2} \Sigma_{i=1}^n \theta_i^2$\
Comme pour la question 1),\
$\nabla f(\theta) = 0 => \forall k=1,...,p: \frac{\partial f(\theta)}{\partial \theta_k}=0$\
$\frac{\partial f(\theta)}{\partial \theta_k}=2\frac{1}{2} (-X_{i,k}) \Sigma_{i=1}^n (Y_i-\Sigma_{j=1}^pX_{i,j}\theta_j)+2\frac{\lambda}{2} \theta_k$\
$~~~~~~~=-\Sigma_{i=1}^n(X_{i,k}Y_i-X_{i,k}X_i\theta)+\lambda \theta_k$\
Donc
$\nabla f(\theta)=-\Sigma_{i=1}^n(X_i^TY_i-X_i^TX_i\theta)+\lambda \theta=-X^TY+X^TX\theta + \lambda \theta$\
Ainsi $\nabla f(\theta)=0 => -X^TY+X^TX\theta + \lambda \theta=0$\
$=> (X^TX + \lambda Id_n)\theta = X^TY => \theta = (X^TX + \lambda Id_n)^{-1} X^TY = \hat{\theta}_{n,\lambda}^{Ridge}$\
