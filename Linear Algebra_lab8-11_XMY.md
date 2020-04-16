

```python
import numpy as np
from numpy import linalg as LA
```

# 8 Eigenvalues and Eigenvectors

---

Find eigenvalues of the following matrices and their associated eigenvectors. Use Mathematica to check your answers.

For a square matrix $A$, an Eigenvector $\vec v$ and Eigenvalue $\lambda$ make this equation true: 
$$A\vec v = \lambda \vec v $$
We can rewrite the equation as follows:
$$A\vec v -  \lambda \vec v = \vec 0\\
(A-\lambda I) \cdot \vec v = \vec 0
$$

where $I$ is the identity matrix of the same dimensions as $A$. Since $\vec v \neq \vec 0 $, to make this equation exists, $\vec v$ has to sit at the null space of the matrix $(A-\lambda I) $. This means that the matrix $(A-\lambda I) $ is not of full rank, or

$$det(A-\lambda I)=0$$

Eigenvectors can be normalized to a vector with length 1.


## 1. $\begin{bmatrix} 2&1\\0&3 \end{bmatrix}$

$$det \begin{vmatrix} \begin{bmatrix} 2&1\\0&3 \end{bmatrix} - \begin{bmatrix} \lambda\\\lambda \end{bmatrix} \cdot \begin{bmatrix} 1&0\\0&1 \end{bmatrix}  \end{vmatrix}= det \begin{vmatrix} 2-\lambda&1\\0&3-\lambda \end{vmatrix} = (2-\lambda)(3-\lambda)=0 $$

Therefore, the two eigenvalues are $\lambda_{1}=2$, $\lambda_{2}=3$. 

- When $\lambda_{1}=2$, 
$\begin{bmatrix} 2-2&1\\0&3-2 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix}  = \begin{bmatrix} 0&1\\0&1 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix} =  \begin{bmatrix} 0\\0\end{bmatrix} $, $v_{2}=0 $, and if normalized, $v_{1}^2 + v_{2}^2 = 1 $. Therefore $v_{1}=1$. 

- When $\lambda_{1}=3$, 
$\begin{bmatrix} -1&1\\0&0 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix}  = \begin{bmatrix} 0\\0\end{bmatrix} $, so $v_{1}=v_{2} $, and if standardized, $v_{1}^2 + v_{2}^2 = 1 $. We can thus get $v_{1}=v_{2} = \frac{\sqrt2}{2}$ . 

The two standardized eigenvectors are thus $\vec v_{1} = (1, 0)$ and $\vec v_{2} = (\frac{\sqrt2}{2}, \frac{\sqrt2}{2})$. 

<br>

## 2. $\begin{bmatrix} 0&0\\0&0 \end{bmatrix}$

$$ det \begin{vmatrix} 0-\lambda&0\\0&0-\lambda \end{vmatrix} = (-\lambda)(-\lambda)=0 $$

The eigenalue of this matrix is $\lambda=0$. 

Therefore $\begin{bmatrix} 0&0\\0&0 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix}  =  \begin{bmatrix} 0\\0\end{bmatrix} $. The eigenvectors of the matrix can be any vectors. 

The two standardized eigenvectors are thus $\vec v_{1} = (1, 0)$ and $\vec v_{2} = (0, 1)$. 



```python
w1, v1 = LA.eig(np.matrix([[2,1],
                           [0,3]]))
print("\n 1. \n Eigenvalues ",w1, "\n Eigenvectors", v1)

w2, v2 = LA.eig(np.matrix([[0,0],
                           [0,0]]))
print("\n 2. \n Eigenvalues ",w2, "\n Eigenvectors", v2)
```

    
     1. 
     Eigenvalues  [2. 3.] 
     Eigenvectors [[1.         0.70710678]
     [0.         0.70710678]]
    
     2. 
     Eigenvalues  [0. 0.] 
     Eigenvectors [[1. 0.]
     [0. 1.]]


## 3. $\begin{bmatrix} 3&2\\6&-1 \end{bmatrix}$

$$ det \begin{vmatrix} 3-\lambda&2\\6&-1-\lambda \end{vmatrix} = (3-\lambda)(-1-\lambda) - 12 =0 \\
-3+ \lambda -3\lambda +\lambda^2-12 = 0\\
\lambda^2 - 2\lambda -15 = 0\\
(\lambda+3)(\lambda-5)=0
$$

The eigenalue of this matrix is $\lambda_{1}=-3$, $\lambda_{2}=5$. 

When $\lambda_{1}=-3$, 

$$\begin{bmatrix} 3-(-3)&2\\6&-1-(-3) \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix}  = \begin{bmatrix} 6&2\\6&2 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix} =  \begin{bmatrix} 6v_{1} + 2 v_{2}\\6v_{1} + 2v_{2}  \end{bmatrix} = \begin{bmatrix} 0\\0\end{bmatrix} \\
v_{2} = - 3v_{1} \\
v_{1}^2 + v_{2}^2  = v_{1}^2 + (-3v_{1})^2 = 10v_{1}^2 = 1$$

Therefore, $v_{1} = \frac{\sqrt10}{10}$, $v_{2} = -\frac{3 \sqrt10}{10}$

When $\lambda_{2}=5$, 

$$\begin{bmatrix} 3-5&2\\6&-1-5 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix}  = \begin{bmatrix} -2&2\\6&-6 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix} =  \begin{bmatrix} -2v_{1} + 2 v_{2}\\6v_{1}  -6v_{2} \end{bmatrix} = \begin{bmatrix} 0\\0\end{bmatrix} \\
 + = 0\\
v_{2} = v_{1} \\
v_{1}^2 + v_{2}^2  = 2v_{1}^2  = 1$$

Therefore, $v_{1} = \frac{\sqrt2}{2}$, $v_{2} = \frac{\sqrt2}{2}$

The two standardized eigenvectors are thus $\vec v_{1} = (\frac{\sqrt10}{10}, -\frac{3 \sqrt10}{10})$ and $\vec v_{2} = (\frac{\sqrt2}{2}, \frac{\sqrt2}{2})$. 

<br>

## 4. $\begin{bmatrix} 1&2\\3&2 \end{bmatrix}$

$$ det \begin{vmatrix} 1-\lambda&2\\3&2-\lambda \end{vmatrix} = (1-\lambda)(2-\lambda) - 6 =0 \\
2-2\lambda -\lambda +\lambda^2-6 = 0\\
\lambda^2 - 3\lambda -4 = 0\\
(\lambda+1)(\lambda-4)=0
$$

The eigenalue of this matrix is $\lambda_{1}=-1$, $\lambda_{2}=4$. 

When $\lambda_{1}=-1$, 

$$\begin{bmatrix} 1-(-1)&2\\3&2-(-1) \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix}  = \begin{bmatrix} 2&2\\3&3 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix} =  \begin{bmatrix} 2v_{1} + 2 v_{2}\\3v_{1} + 3v_{2} \end{bmatrix} = \begin{bmatrix} 0\\0\end{bmatrix} \\
v_{2} = - v_{1} \\
v_{1}^2 + v_{2}^2  = 2v_{1}^2 = 1$$

Therefore, $v_{1} = \frac{\sqrt2}{2}$, $v_{2} = -\frac{\sqrt2}{2}$

When $\lambda_{1}=4$, 

$$\begin{bmatrix} 1-4&2\\3&2-4 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix}  = \begin{bmatrix} -3&2\\3&-2 \end{bmatrix} \cdot \begin{bmatrix} v_{1}\\v_{2} \end{bmatrix} \begin{bmatrix} -3v_{1} + 2 v_{2}\\3v_{1} -2 v_{2} \end{bmatrix} =  \begin{bmatrix} 0\\0\end{bmatrix} \\
v_{2} = - \frac{3}{2}v_{1} \\
v_{1}^2 + v_{2}^2  = v_{1}^2 + (\frac{2}{3}v_{1})^2 = \frac{13}{9}v_{1}^2 = 1$$

Therefore, $v_{1} = \frac{\sqrt10}{10}$, $v_{2} = -\frac{3 \sqrt10}{10}$

The two standardized eigenvectors are thus $\vec v_{1} = span(\frac{\sqrt2}{2}, -\frac{\sqrt2}{2})$ and $\vec v_{2} = span(\frac{\sqrt10}{10}, -\frac{3 \sqrt10}{10})$. 






```python
w3, v3 = LA.eig(np.matrix([[3,2],
                           [6,-1]]))
print("\n 3. \n Eigenvalues ",w3, "\n Eigenvectors \n", v3)

w4, v4 = LA.eig(np.matrix([[1,2],
                           [3,2]]))
print("\n 4. \n Eigenvalues ",w4, "\n Eigenvectors \n", v4)
```

    
     3. 
     Eigenvalues  [ 5. -3.] 
     Eigenvectors 
     [[ 0.70710678 -0.31622777]
     [ 0.70710678  0.9486833 ]]
    
     4. 
     Eigenvalues  [-1.  4.] 
     Eigenvectors 
     [[-0.70710678 -0.5547002 ]
     [ 0.70710678 -0.83205029]]


## 5. $\begin{bmatrix} 2&1&0\\0&2&0\\2&3&1 \end{bmatrix}$

$$ det \begin{vmatrix} \begin{bmatrix} 2&1&0\\0&2&0\\2&3&1 \end{bmatrix} - \begin{bmatrix} \lambda&0&0\\0&\lambda&0\\0&0&\lambda \end{bmatrix} \end{vmatrix} = det \begin{vmatrix} 2-\lambda&1&0\\0&2-\lambda&0\\2&3&1-\lambda \end{vmatrix} = (2-\lambda)(2-\lambda)(1-\lambda) =0 \\
$$

The three eigenalue of this matrix is $\lambda_{1}=1$, $\lambda_{2}=\lambda_{3}=2$. 

When $\lambda_{1}=1$, 

$$\begin{bmatrix} 2-1&1&0\\0&2-1&0\\2&3&1-1 \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v{3} \end{bmatrix} = \begin{bmatrix} v_{1} + v_{2}\\ v_{2}\\2v_{1}+3v_{2} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}= v_{2}=0\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$. 

Therefore, $v_{1}= v_{2}=0$, $v_{3}=1$. 

When $\lambda_{2}=\lambda_{3}=2$, 

$$\begin{bmatrix} 2-2&1&0\\0&2-2&0\\2&3&1-2 \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v{3} \end{bmatrix} = \begin{bmatrix}  v_{2}\\ 0\\2v_{1}+3v_{2}- v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{2}=0\\
2v_{1}=v_{3}\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$. 

Therefore, $v_{1}=\frac{1}{\sqrt5}, v_{2}=0$, $v_{3}=\frac{2}{\sqrt5}$. 

The three standardized eigenvectors are thus $\vec v_{1} = span \left( 0,0,1\right)$ and $\vec v_{2} = \vec v_{3} = span(\frac{1}{\sqrt5},0,\frac{2}{\sqrt5})$. 



```python
w5, v5 = LA.eig(np.matrix([[2,1,0],
                         [0,2,0],
                         [2,3,1]]))
print("\n 5. \n Eigenvalues ",w5, "\n Eigenvectors \n", v5)
```

    
     5. 
     Eigenvalues  [1. 2. 2.] 
     Eigenvectors 
     [[ 0.00000000e+00  4.47213595e-01 -4.47213595e-01]
     [ 0.00000000e+00  0.00000000e+00  1.98602732e-16]
     [ 1.00000000e+00  8.94427191e-01 -8.94427191e-01]]


## 6. $\begin{bmatrix} 4&2&-2\\-5&3&2\\-2&4&1 \end{bmatrix}$

$$ det \begin{vmatrix} \begin{bmatrix} 4&2&-2\\-5&3&2\\-2&4&1 \end{bmatrix} - \begin{bmatrix} \lambda&0&0\\0&\lambda&0\\0&0&\lambda \end{bmatrix} \end{vmatrix} = det \begin{vmatrix} 4-\lambda&2&-2\\-5&3-\lambda&2\\-2&4&1-\lambda \end{vmatrix}\\ = (4-\lambda)(3-\lambda)(1-\lambda)-8+20-(-10)(1-\lambda)-8(4-\lambda)-4(3-\lambda) \\
=(\lambda-5)(\lambda-2)(\lambda-1)=0 \\
$$

The three eigenalue of this matrix is $\lambda_{1}=5$, $\lambda_{2}=2, \lambda_{3}=1$. 

When $\lambda_{1}=5$, 

$$\begin{bmatrix}4-5 &2&-2\\-5&3-5&2\\-2&4&1-5  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v{3} \end{bmatrix} = \begin{bmatrix} -v_{1} + 2v_{2}- 2v_{3}\\ -5v_{1}-2v_{2}+2v_{3}\\-2v_{1}+4v_{2}+3v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}= 2v_{2}-v_{3}=0\\
(-2)(2v_{2}-v_{3})+4v_{2}+3v_{3} = 5v_{3}=0\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$. 

Therefore, $v_{1}= v_{2}=\frac{1}{\sqrt2}$, $v_{3}=0$. 

When $\lambda_{2}=2$, 

$$\begin{bmatrix}4-2 &2&-2\\-5&3-2&2\\-2&4&1-2 \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v{3} \end{bmatrix} = \begin{bmatrix}2v_{1} + 2v_{2}- 2v_{3}\\ -5v_{1}+v_{2}+2v_{3}\\-2v_{1}+4v_{2}-v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}=v_{2}\\
v_{3}= v_{1}+ v_{2}\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=v_{2}=\frac{1}{\sqrt6}$, $v_{3}=\frac{2}{\sqrt6}$. 

When $\lambda_{2}=1$, 

$$\begin{bmatrix}4-1 &2&-2\\-5&3-1&2\\-2&4&1-1 \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v{3} \end{bmatrix} = \begin{bmatrix}3v_{1} + 2v_{2}- 2v_{3}\\ -5v_{1}+2v_{2}+2v_{3}\\-2v_{1}+4v_{2} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}=2v_{2}\\
v_{3}= 4v_{2}=\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{2}{\sqrt21}, v_{2}=\frac{1}{\sqrt21}$, $v_{3}=\frac{4}{\sqrt21}$. 

The three standardized eigenvectors are thus $\vec v_{1} = span(\frac{1}{\sqrt2}, \frac{1}{\sqrt2},v_{3}=0)$, $\vec v_{2} = span(\frac{1}{\sqrt6}, \frac{1}{\sqrt6}, \frac{2}{\sqrt6})$, and $\vec v_{3} = span(\frac{2}{\sqrt21}, \frac{1}{\sqrt21}, \frac{4}{\sqrt21})$. 



```python
w6, v6 = LA.eig(np.matrix([[4,2,1],
                           [-5,3,2],
                           [-1,4,1]]))
print("\n 6. \n Eigenvalues ",w6, "\n Eigenvectors \n", v6)
```

    
     6. 
     Eigenvalues  [ 4.5+3.27871926j  4.5-3.27871926j -1. +0.j        ] 
     Eigenvectors 
     [[-5.44347183e-03-0.53542848j -5.44347183e-03+0.53542848j
       5.02674854e-17+0.j        ]
     [ 6.42329676e-01+0.j          6.42329676e-01-0.j
      -4.47213595e-01+0.j        ]
     [ 4.68138577e-01-0.28556186j  4.68138577e-01+0.28556186j
       8.94427191e-01+0.j        ]]


## 7. $\begin{bmatrix} 1&2&3\\0&4&5\\0&0&6 \end{bmatrix}$


$$ det \begin{vmatrix} \begin{bmatrix} 1&2&3\\0&4&5\\0&0&6 \end{bmatrix} - \begin{bmatrix} \lambda&0&0\\0&\lambda&0\\0&0&\lambda \end{bmatrix} \end{vmatrix} = det \begin{vmatrix} 1-\lambda &2&3\\0&4-\lambda &5\\0&0&6-\lambda  \end{vmatrix}\\ = (1-\lambda)(4-\lambda)(6-\lambda)=0 \\
$$

The three eigenalue of this matrix is $\lambda_{1}=1$, $\lambda_{2}=4, \lambda_{3}=6$. 

When $\lambda_{1}=1$, 

$$\begin{bmatrix} 1-1&2&3\\0&4-1&5\\0&0&6-1  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} 2v_{2}+3v_{3}\\3v_{2}+5v_{3}\\5v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{2}=v_{3}=0\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=1, v_{2}=v_{3}=0$. 

When $\lambda_{2}=4$, 

$$\begin{bmatrix} 1-4&2&3\\0&4-4&5\\0&0&6-4  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} -3v_{1}+ 2v_{2}+3v_{3}\\5v_{3}\\2v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
-3v_{1}+2v_{2}=0\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{2}{\sqrt13}, v_{2}=\frac{3}{\sqrt13}, v_{3}=0$. 

When $\lambda_{3}=6$, 

$$\begin{bmatrix} 1-6&2&3\\0&4-6&5\\0&0&6-6  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} -5v_{1}+ 2v_{2}+3v_{3}\\-2v_{2}+5v_{3}\\0 \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{2}=\frac{5}{2}v_{3}\\
v_{1}=\frac{8}{5}v_{3}\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{12}{25}\sqrt109, v_{2}=\frac{3}{4}\sqrt109, v_{3}=\frac{3}{10}\sqrt109$. 

The three eigenvectors for this matrix is $\vec v_{1}= span(1,0,0), \vec v_{2} = span(\frac{2}{\sqrt13},\frac{3}{\sqrt13}, 0),  \vec v_{3}=span(\frac{12}{25}\sqrt109, \frac{3}{4}\sqrt109, \frac{3}{10}\sqrt109)$




```python
w7, v7 = LA.eig(np.matrix([[1,2,3],
                           [0,4,5],
                           [0,0,6]]))
print("\n 7. \n Eigenvalues ",w7, "\n Eigenvectors \n", v7)
```

    
     7. 
     Eigenvalues  [1. 4. 6.] 
     Eigenvectors 
     [[1.         0.5547002  0.51084069]
     [0.         0.83205029 0.79818857]
     [0.         0.         0.31927543]]





    10.44030650891055



## 8. $\begin{bmatrix} 1&-1&-1\\1&3&1\\-3&1&-1 \end{bmatrix}$

$$ det \begin{vmatrix} \begin{bmatrix} 1&-1&-1\\1&3&1\\-3&1&-1 \end{bmatrix} - \begin{bmatrix} \lambda&0&0\\0&\lambda&0\\0&0&\lambda \end{bmatrix} \end{vmatrix} = det \begin{vmatrix} 1-\lambda&-1&-1\\1&3-\lambda&1\\-3&1&-1-\lambda  \end{vmatrix}\\ = \lambda^3-3\lambda^2+2\lambda-12=0 \\
$$

The three eigenalue of this matrix is $\lambda_{1}=2$, $\lambda_{2}=-2, \lambda_{3}=3$. 

When $\lambda_{1}=2$, 

$$\begin{bmatrix} 1-2&-1&-1\\1&3-2&1\\-3&1&-1-2  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} -v_{1}-v_{2}-v_{3}\\v_{1}+v_{2}+v_{3}\\-3v_{1}+v_{2}-v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=0, v_{2}=-\frac{1}{\sqrt2}, v_{3}=\frac{1}{\sqrt2}$. 

When $\lambda_{2}=-2$, 

$$\begin{bmatrix} 1+2&-1&-1\\1&3+2&1\\-3&1&-1+2  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} 3v_{1}-v_{2}-v_{3}\\v_{1}+5v_{2}+v_{3}\\-3v_{1}+v_{2}+v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}=-v_{2}\\
v_{3}=-4v_{1}\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{\sqrt2}{6}, v_{2}=-\frac{\sqrt2}{6}, v_{3}=\frac{2\sqrt2}{3}$. 

When $\lambda_{3}=3$, 

$$\begin{bmatrix} 1-3&-1&-1\\1&3-3&1\\-3&1&-1-3  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} -2v_{1}-v_{2}-v_{3}\\v_{1}+v_{3}\\-3v_{1}+v_{2}-4v_{3}\end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}=-v_{3}\\
v_{2}=v_{1}\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=-\frac{1}{\sqrt3}, v_{2}=-\frac{1}{\sqrt3}, v_{3}=-\frac{1}{\sqrt3}$. 

The three eigenvectors for this matrix is $\vec v_{1}= span(0, -\frac{1}{\sqrt2},\frac{1}{\sqrt2}), \vec v_{2} = span(\frac{\sqrt2}{6}, -\frac{\sqrt2}{6}, \frac{2\sqrt2}{3}),  \vec v_{3}=span(-\frac{1}{\sqrt3}, \frac{1}{\sqrt3}, \frac{1}{\sqrt3})$


```python
w8, v8 = LA.eig(np.matrix([[1,-1,-1],
                           [1,3,1],
                           [-3,1,-1]]))
print("\n 8. \n Eigenvalues ",w8, "\n Eigenvectors \n", v8)
```

    
     8. 
     Eigenvalues  [-2.  2.  3.] 
     Eigenvectors 
     [[ 2.35702260e-01 -7.07106781e-01 -5.77350269e-01]
     [-2.35702260e-01  7.45148041e-16  5.77350269e-01]
     [ 9.42809042e-01  7.07106781e-01  5.77350269e-01]]


## 9. $\begin{bmatrix} 1&0&0&0\\2&-1&0&0\\5&3&2&0\\7&4&6&2 \end{bmatrix}$


```python
w9, v9 = LA.eig(np.matrix([[1,0,0,0],
                           [2,-1,0,0],
                           [5,3,2,0],
                           [7,4,6,2]]))
print("\n 9. \n Eigenvalues ",w9, "\n Eigenvectors \n", v9)
```

    
     9. 
     Eigenvalues  [ 2.  2. -1.  1.] 
     Eigenvectors 
     [[ 0.00000000e+00  0.00000000e+00  0.00000000e+00  2.63981839e-02]
     [ 0.00000000e+00  0.00000000e+00  6.39602149e-01  2.63981839e-02]
     [ 0.00000000e+00  7.40148683e-17 -6.39602149e-01 -2.11185471e-01]
     [ 1.00000000e+00 -1.00000000e+00  4.26401433e-01  9.76732803e-01]]


# 9 Properties of Eigenvalues and Eigenvectors

---

Let $A$ be the following matrix: $$\begin{bmatrix} 1&1&-1\\2&3&-4\\4&1&-4 \end{bmatrix}$$

Use Maple to do the following:


## 1. Find the eigenvalues of $A$ and their associated eigenvectors

$$ det \begin{vmatrix} \begin{bmatrix} 1&1&-1\\2&3&-4\\4&1&-4 \end{bmatrix} - \begin{bmatrix} \lambda&0&0\\0&\lambda&0\\0&0&\lambda \end{bmatrix} \end{vmatrix} = det \begin{vmatrix} 1-\lambda&1&-1\\2&3-\lambda&-4\\4&1&-4-\lambda \end{vmatrix} \\
(1-\lambda)(3-\lambda)(-4-\lambda)-16-2-2(-4-\lambda)+4(1-\lambda)+4(3-\lambda)=0
$$


The three eigenalue of this matrix is $\lambda_{1}=2$, $\lambda_{2}=1, \lambda_{3}=-3$. 

When $\lambda_{1}=2$, 

$$\begin{bmatrix}1-2&1&-1\\2&3-2&-4\\4&1&-4-2 \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} -v_{1}+v_{2}-v_{3}\\2v_{1}+v_{2}-4v_{3}\\4v_{1}+v_{2}-6v_{3}\end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{1}{\sqrt6}, v_{2}=\frac{2}{\sqrt6}, v_{3}=\frac{1}{\sqrt6}$. 

When $\lambda_{2}=1$, 

$$\begin{bmatrix} 1-1&1&-1\\2&3-1&-4\\4&1&-4-1  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} v_{2}-v_{3}\\2v_{1}+2v_{2}-4v_{3}\\4v_{1}+v_{2}-5v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=v_{2}=v_{3}=\frac{1}{\sqrt3}$. 

When $\lambda_{3}=-3$, 

$$\begin{bmatrix} 1+3&1&-1\\2&3+3&-4\\4&1&-4+3  \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} 4v_{1} + v_{2}-v_{3}\\2v_{1}+6v_{2}-4v_{3}\\4v_{1}+v_{2}-v_{3}\end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}=-v_{3}\\
v_{2}=v_{1}\\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{\sqrt19}{57}, v_{2}=\frac{7\sqrt19}{57}, v_{3}=\frac{11\sqrt19}{57}$. 

The three eigenvectors for this matrix is $\vec v_{1}= span(\frac{1}{\sqrt6},\frac{2}{\sqrt6},\frac{1}{\sqrt6}), \vec v_{2} = span(\frac{1}{\sqrt3}, \frac{1}{\sqrt3}, \frac{1}{\sqrt3}),  \vec v_{3}=span(\frac{\sqrt19}{57}, \frac{7\sqrt19}{57}, \frac{11\sqrt19}{57})$

<br>

## 2. Standardize the eigenvectors.

The standardized eigenvectors are $\vec v_{1}=\begin {bmatrix} \frac{1}{\sqrt6}\\\frac{2}{\sqrt6}\\\frac{1}{\sqrt6}\end{bmatrix}$, $\vec v_{2} = \begin {bmatrix} \frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\\ \frac{1}{\sqrt3}\end{bmatrix}$, $\vec v_{3}=\begin {bmatrix} \frac{\sqrt19}{57}
\\ \frac{7\sqrt19}{57}\\\frac{11\sqrt19}{57}\end{bmatrix}$






```python
w, v = LA.eig(np.matrix([[1,1,-1],
                         [2,3,-4],
                         [4,1,-4]]))
print("eigenvalue: \n", w, "\n eigenvector: \n", v.round(decimals=4))
```

    eigenvalue: 
     [-3.  1.  2.] 
     eigenvector: 
     [[ 0.0765  0.5774 -0.4082]
     [ 0.5353  0.5774 -0.8165]
     [ 0.8412  0.5774 -0.4082]]


## 3. Show that the eigenvectors are orthogonal to each other.
 
Eigenvectors are not orthogonal to each other for matrix $A$ because $A$ is not symmetric.




```python
np.matrix([0.076,0.577,-0.408]).T * np.matrix([0.076,0.577,-0.408])
```




    matrix([[ 0.005776,  0.043852, -0.031008],
            [ 0.043852,  0.332929, -0.235416],
            [-0.031008, -0.235416,  0.166464]])



## 4. Find the trace of $A$. Verify that it is equal to the sum of the eigenvalues.

$$tr(A) = \sum_{n=1}^{n}A_{n*n} = a_{11} + a_{22} + \cdots + a_{nn} = 1+3+(-4) = 0$$

$$\sum (eig) = 2+1+(-3)=0$$

<br>

## 5. Find the determinant of $A$. Verify that it is equal to the product of the eigenvalues.

$$det|A| = det \begin{vmatrix} 1&1&-1\\2&3&-4\\4&1&-4 \end{vmatrix} = -12-16-2+8+4+12=-6$$

$$\prod(eig) = 2*1*(-3)=-6 $$

<br>

## 6. Find the rank of $A$. Verify that it is equal to the number of non-zero eigenvalues.

$$\begin{bmatrix} 1&1&-1\\2&3&-4\\4&1&-4 \end{bmatrix} 
\xrightarrow[R_{3}+(-4)R_{1} \rightarrow R_{3}]{R_{2}+(-2)R_{1} \rightarrow R_{2}} 
\begin{bmatrix} 1&1&-1\\0&1&-2\\0&-3&0 \end{bmatrix} 
\xrightarrow[]{R_{3}+3R_{2} \rightarrow R_{3}} 
\begin{bmatrix} 1&1&-1\\0&1&-2\\0&0&-6 \end{bmatrix}
\xrightarrow[]{-\frac{1}{6}R_{3}} 
\begin{bmatrix} 1&1&-1\\0&1&-2\\0&0&1 \end{bmatrix}
$$

Therefore, $rank(A) = 3$, and matrix $A$ hs 3 non-zero eigenvalues. 







## 7. Find the eigenvalues of $A^2$ and their associated eigenvectors. How do they compare with the eigenvalues and eigenvectors of $A$?

$$A^2 = A\prime \times A = \begin{bmatrix} 1&2&4\\1&3&1\\-1&-4&-4 \end{bmatrix} \times \begin{bmatrix} 1&1&-1\\2&3&-4\\4&1&-4 \end{bmatrix} =\begin{bmatrix} -1&3&-1\\-8&7&2\\-10&3&8 \end{bmatrix}  $$

The eigenvalues of matrix $A^2$ is $\lambda_{1} = 9, \lambda_{2} = 1,\lambda_{3} = 3 $. They are also the square of the eigenvalues of the original matrix $A$.

The eigenvectors of matrix $A^2$ and $A$ are identical, both are $\vec v_{1}=\begin {bmatrix} \frac{1}{\sqrt6}\\\frac{2}{\sqrt6}\\\frac{1}{\sqrt6}\end{bmatrix}$, $\vec v_{2} = \begin {bmatrix} \frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\\ \frac{1}{\sqrt3}\end{bmatrix}$, $\vec v_{3}=\begin {bmatrix} \frac{\sqrt19}{57}
\\ \frac{7\sqrt19}{57}\\\frac{11\sqrt19}{57}\end{bmatrix}$

<br>

## 8. Find the eigenvalues of $A^{-1}$ and their associated eigenvectors. How do they compare with the eigenvalues and eigenvectors of $A$?

$$adj(A) = \begin{bmatrix} -8&-8&-10\\-(-3)&0&-(-3)\\-1&-(-2)&1 \end{bmatrix} \prime = \begin{bmatrix} -8&3&-1\\-8&0&2\\-10&3&1 \end{bmatrix} $$

$$det(A)=-6$$

$$A^{-1} = \frac{1}{det(A)} adj(A) = \begin{bmatrix} \frac{4}{3}&-\frac{1}{2}&\frac{1}{6}\\\frac{4}{3}&0&-\frac{1}{3}\\\frac{5}{3}&-\frac{1}{2}&-\frac{1}{6} \end{bmatrix}$$

The eigenvalues of $A^{-1}$ are $\lambda_{1} = -\frac{1}{3}, \lambda_{2} = 1, \lambda_{3} = \frac{1}{2}$. They are the inverse of the eigenvalues of original matrix $A$.

The eigenvectors of matrix $A^{-1}$ and $A$ are also identical $\vec v_{1}=\begin {bmatrix} \frac{1}{\sqrt6}\\\frac{2}{\sqrt6}\\\frac{1}{\sqrt6}\end{bmatrix}$, $\vec v_{2} = \begin {bmatrix} \frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\\ \frac{1}{\sqrt3}\end{bmatrix}$, $\vec v_{3}=\begin {bmatrix} \frac{\sqrt19}{57}
\\ \frac{7\sqrt19}{57}\\\frac{11\sqrt19}{57}\end{bmatrix}$



```python
print("A^2: \n", LA.matrix_power(np.matrix([[1,1,-1],[2,3,-4],[4,1,-4]]), n=2))
print("\n A.inv: \n", LA.inv(np.matrix([[1,1,-1],[2,3,-4],[4,1,-4]])))
print("\n eig(A^2): \n", LA.eig(LA.matrix_power(np.matrix([[1,1,-1],[2,3,-4],[4,1,-4]]), n=2)))
print("\n eig(A.inv): \n", LA.eig(LA.inv(np.matrix([[1,1,-1],[2,3,-4],[4,1,-4]]))))
print("\n eig(A): \n", LA.eig(np.matrix([[1,1,-1],[2,3,-4],[4,1,-4]])))
```

    A^2: 
     [[ -1   3  -1]
     [ -8   7   2]
     [-10   3   8]]
    
     A.inv: 
     [[ 1.33333333 -0.5         0.16666667]
     [ 1.33333333  0.         -0.33333333]
     [ 1.66666667 -0.5        -0.16666667]]
    
     eig(A^2): 
     (array([9., 1., 4.]), matrix([[ 0.07647191,  0.57735027, -0.40824829],
            [ 0.53530338,  0.57735027, -0.81649658],
            [ 0.84119102,  0.57735027, -0.40824829]]))
    
     eig(A.inv): 
     (array([-0.33333333,  1.        ,  0.5       ]), matrix([[-0.07647191, -0.57735027, -0.40824829],
            [-0.53530338, -0.57735027, -0.81649658],
            [-0.84119102, -0.57735027, -0.40824829]]))
    
     eig(A): 
     (array([-3.,  1.,  2.]), matrix([[ 0.07647191,  0.57735027, -0.40824829],
            [ 0.53530338,  0.57735027, -0.81649658],
            [ 0.84119102,  0.57735027, -0.40824829]]))


# 10 More Properties of Eigenvalues and Eigenvectors

---


Let $A$ be the following matrix $A= \begin{bmatrix} 2&4&2\\4&0&4\\2&4&2 \end{bmatrix}$. 

Use Maple to do the following:

## 1. Find the eigenvalues of $A$ and their associated eigenvectors.

## 2. Standardize the eigenvectors.

$$ det \begin{vmatrix} \begin{bmatrix} 2&4&2\\4&0&4\\2&4&2  \end{bmatrix} - \begin{bmatrix} \lambda&0&0\\0&\lambda&0\\0&0&\lambda \end{bmatrix} \end{vmatrix} = det \begin{vmatrix} 2-\lambda&4&2\\4&0-\lambda&4\\2&4&2-\lambda  \end{vmatrix} \\
(2-\lambda)(-\lambda)(2-\lambda)-32-32-16(2-\lambda)-16(2-\lambda)-4(-\lambda)=0
$$


The three eigenalue of this matrix is $\lambda_{1}=8$, $\lambda_{2}=0, \lambda_{3}=-4$. 

When $\lambda_{1}=8$, 

$$\begin{bmatrix}2-8&4&2\\4&0-8&4\\2&4&2-8 \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} -6v_{1}+4v_{2}+2v_{3}\\4v_{1}-8v_{2}+4v_{3}\\2v_{1}+4v_{2}-6v_{3}\end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=v_{2}=v_{3}=\frac{1}{\sqrt3}$. 

When $\lambda_{2}=0$, 

$$\begin{bmatrix} 2-0&4&2\\4&0-0&4\\2&4&2-0   \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} 2v_{1}+ 4v_{2}+2v_{3}\\4v_{1}+4v_{3}\\2v_{1}4v_{2}+2v_{3} \end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{1}{\sqrt2}, v_{2}=0, v_{3}=-\frac{1}{\sqrt2}$. 

When $\lambda_{3}=-4$, 

$$\begin{bmatrix} 2+4&4&2\\4&0+4&4\\2&4&2+4 \end{bmatrix} \cdot \begin{bmatrix}v_{1}\\v_{2}\\v_{3} \end{bmatrix} = \begin{bmatrix} 6v_{1} +4v_{2}+2v_{3}\\4v_{1}+4v_{2}+4v_{3}\\2v_{1}+6v_{2}-4v_{3}\end{bmatrix} = \begin{bmatrix} 0\\ 0\\0 \end{bmatrix} \\
v_{1}^2 + v_{2}^2 +v_{3}^2 =1$$ 

Therefore, $v_{1}=\frac{1}{\sqrt6}, v_{2}=-\frac{2}{\sqrt6}, v_{3}=\frac{1}{\sqrt6}$. 

The three standardized eigenvectors are $\vec v_{1}=\begin {bmatrix} \frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\end{bmatrix}$, $\vec v_{2} = \begin {bmatrix}\frac{1}{\sqrt2}\\0\\-\frac{1}{\sqrt2} \end{bmatrix}$, $\vec v_{3}=\begin {bmatrix} \frac{1}{\sqrt6}\\-\frac{2}{\sqrt6}\\\frac{1}{\sqrt6}\end{bmatrix}$



```python
LA.eig(np.matrix([[2,4,2],
                  [4,0,4],
                  [2,4,2]]))
```




    (array([ 8.00000000e+00, -3.51535614e-17, -4.00000000e+00]),
     matrix([[-5.77350269e-01, -7.07106781e-01,  4.08248290e-01],
             [-5.77350269e-01, -6.78782813e-17, -8.16496581e-01],
             [-5.77350269e-01,  7.07106781e-01,  4.08248290e-01]]))



## 3. Show that the eigenvectors are orthogonal to each other.

$$\vec v_{1} \times \vec v_{2} = \begin {bmatrix} \frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\end{bmatrix} \times \begin {bmatrix}\frac{1}{\sqrt2}\\0\\-\frac{1}{\sqrt2} \end{bmatrix} = \frac{1}{\sqrt3}*\frac{1}{\sqrt2} +0 -\frac{1}{\sqrt3}*\frac{1}{\sqrt2} =  0$$

$$\vec v_{1} \times \vec v_{3} = \begin {bmatrix} \frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\end{bmatrix} \times \begin {bmatrix} \frac{1}{\sqrt6}\\-\frac{2}{\sqrt6}\\\frac{1}{\sqrt6} \end{bmatrix} = \frac{1}{\sqrt3} * \frac{1}{\sqrt6} - \frac{1}{\sqrt3} * \frac{2}{\sqrt6} + \frac{1}{\sqrt3} * \frac{1}{\sqrt6} = 0$$

$$\vec v_{2} \times \vec v_{3} = \begin {bmatrix} \frac{1}{\sqrt2}\\0\\-\frac{1}{\sqrt2}\end{bmatrix} \times \begin {bmatrix} \frac{1}{\sqrt6}\\-\frac{2}{\sqrt6}\\\frac{1}{\sqrt6} \end{bmatrix} = \frac{1}{\sqrt2} * \frac{1}{\sqrt6} -0 + \frac{1}{\sqrt2} * \frac{1}{\sqrt6} = 0$$

The eigenvectors are orthogonal to each other is thus proven.

<br>

## 4. Show that for each eigenvector $x_{i}, x_{i}\prime x_{i} = 1$.

$$\vec v_{1} \prime \times \vec v_{1} = \begin {bmatrix} \frac{1}{\sqrt3}&\frac{1}{\sqrt3}&\frac{1}{\sqrt3}\end{bmatrix} \times \begin {bmatrix} \frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\\\frac{1}{\sqrt3}\end{bmatrix} = \frac{1}{\sqrt3} * \frac{1}{\sqrt3} *3 = 1$$

$$\vec v_{2} \prime \times \vec v_{2} = \begin {bmatrix} \frac{1}{\sqrt2}&0&-\frac{1}{\sqrt2} \end{bmatrix} \times \begin {bmatrix} \frac{1}{\sqrt2}\\0\\-\frac{1}{\sqrt2} \end{bmatrix} = \frac{1}{\sqrt2} * \frac{1}{\sqrt2} *2 = 1$$

$$\vec v_{3} \prime \times \vec v_{3} = \begin {bmatrix}  \frac{1}{\sqrt6}&-\frac{2}{\sqrt6}&\frac{1}{\sqrt6} \end{bmatrix} \times \begin {bmatrix}  \frac{1}{\sqrt6}\\-\frac{2}{\sqrt6}\\\frac{1}{\sqrt6} \end{bmatrix} = \frac{1}{\sqrt6} * \frac{1}{\sqrt6} *2 + \frac{2}{\sqrt6} * \frac{2}{\sqrt6} = 1$$


## 5. Let $X = \begin{bmatrix} x_{1} & x_{2} & x_{3}\end{bmatrix}$, where the $x_{i}$ are the eigenvectors. Verify that $X^{-1} = X\prime$.

$$X = \begin {bmatrix} \frac{1}{\sqrt3}& \frac{1}{\sqrt2}&\frac{1}{\sqrt6} \\ \frac{1}{\sqrt3}&0&-\frac{2}{\sqrt6} \\ \frac{1}{\sqrt3}&-\frac{1}{\sqrt2}&\frac{1}{\sqrt6} \end{bmatrix} $$

$$X\prime = \begin {bmatrix} \frac{1}{\sqrt3}&\frac{1}{\sqrt3}&\frac{1}{\sqrt3} \\  \frac{1}{\sqrt2}&0&-\frac{1}{\sqrt2}  \\  \frac{1}{\sqrt6}&-\frac{2}{\sqrt6}&\frac{1}{\sqrt6}\end{bmatrix}$$

$$det|X| = 0$$, therefore $X$ is not invertible.

<br>

## 6. Find $Λ=X\prime AX$, and verify that it is a diagonal matrix.

$$\begin{aligned}
Λ &=  \begin {bmatrix} \frac{1}{\sqrt3}&\frac{1}{\sqrt3}&\frac{1}{\sqrt3} \\  \frac{1}{\sqrt2}&0&-\frac{1}{\sqrt2}  \\  \frac{1}{\sqrt6}&-\frac{2}{\sqrt6}&\frac{1}{\sqrt6}\end{bmatrix} \times \begin{bmatrix} 2&4&2\\4&0&4\\2&4&2 \end{bmatrix} \times \begin {bmatrix} \frac{1}{\sqrt3}& \frac{1}{\sqrt2}&\frac{1}{\sqrt6} \\ \frac{1}{\sqrt3}&0&-\frac{2}{\sqrt6} \\ \frac{1}{\sqrt3}&-\frac{1}{\sqrt2}&\frac{1}{\sqrt6} \end{bmatrix} \\
&=\begin {bmatrix} \frac{8}{\sqrt3}&\frac{8}{\sqrt3}&\frac{8}{\sqrt3}\\ 0&0&0 \\ \frac{-4}{\sqrt6}&\frac{8}{\sqrt6}&\frac{-4}{\sqrt6} \\ \end{bmatrix} \times \begin {bmatrix} \frac{1}{\sqrt3}& \frac{1}{\sqrt2}&\frac{1}{\sqrt6} \\ \frac{1}{\sqrt3}&0&-\frac{2}{\sqrt6} \\ \frac{1}{\sqrt3}&-\frac{1}{\sqrt2}&\frac{1}{\sqrt6} \end{bmatrix}  \\
&= \begin {bmatrix} 8&0&0\\0&0&0\\0&0&4\\ \end {bmatrix}
\end{aligned}$$

Therefore $Λ$ is a diagnal matrix.





```python
X = np.matrix([[-5.77350269e-01, -7.07106781e-01,  4.08248290e-01],
               [-5.77350269e-01, -6.78782813e-17, -8.16496581e-01],
               [-5.77350269e-01,  7.07106781e-01,  4.08248290e-01]])
np.round(X.T * np.matrix([[2,4,2],
                  [4,0,4],
                  [2,4,2]]) * X, decimals=3)
```




    array([[ 8.,  0.,  0.],
           [ 0.,  0., -0.],
           [ 0., -0., -4.]])



## 7. Find the trace of $A$. Verify that it is equal to the sum of the eigenvalues.
$$A = \begin{bmatrix} 2&4&2\\4&0&4\\2&4&2 \end{bmatrix}$$
$$tr(A) = 2+0+2 =4$$
$$\sum_{\lambda_{i}}^{3}=8+0+(-4)=4$$

<br>

## 8. Find the determinant of $A$. Verify that it is equal to the product of the eigenvalues.

$$det(A) = 2*0*2+4*4*2+2*4*4-2*4*4-2*4*4-2*0*2 = 0 $$
$$\prod_{\lambda_{i}}^{3}=8*0*(-4)=0$$

<br>

## 9. Find the rank of $A$. Verify that it is equal to the number of non-zero eigenvalues.

$A$ has 2 non-zero eigenvectors $\lambda_{1}=8, \lambda_{3}=-4$

$$\begin{bmatrix} 2&4&2\\4&0&4\\2&4&2 \end{bmatrix}
\xrightarrow[\frac{1}{2}R_{1}]{R_{2}-2R_{1}, R_{3}-R_{1}}
\begin{bmatrix} 1&2&1\\0&-8&0\\0&0&0 \end{bmatrix}
\xrightarrow[]{-\frac{1}{8}R_{2}}
\begin{bmatrix} 1&2&1\\0&1&0\\0&0&0 \end{bmatrix}
$$

Therefore, $rank(A)=2$. 

<br>

## 10. Find the eigenvalues of $A^2$ and their associated eigenvectors. How do they compare with the eigenvalues and eigenvectors of $A$?

$$A^2=\begin{bmatrix} 24&16&24\\16&32&16\\24&16&24 \end{bmatrix}$$

The eigenvalues of $A^2$ is $\lambda_{1}=64$, $\lambda_{2}=0$, and $\lambda_{3}=16$. They are the square of the eigenvalues of $A$. 

The eigenvectors of $A^2$ are identical to those of $A$.

<br>

## 11. Find the eigenvalues of $A^{-1}$ and their associated eigenvectors. How do they compare with the eigenvalues and eigenvectors of A?

Since $det(A)=0$, the matrix is not inversable
<br>

## 12. Is $A$ idempotent?

The matrix $A$ is idempotent if and only if $A^{2}=A$. Therefore, matrix $A$ is NOT idempotent.


```python
print("A^2: \n", LA.matrix_power(np.matrix([[2,4,2],[4,0,4],[2,4,2]]), n=2))
print("\n")
print("eig(A^2): \n", LA.eig(LA.matrix_power(np.matrix([[2,4,2],[4,0,4],[2,4,2]]), n=2)))
```

    A^2: 
     [[24 16 24]
     [16 32 16]
     [24 16 24]]
    
    
    eig(A^2): 
     (array([ 6.40000000e+01, -6.54261801e-16,  1.60000000e+01]), matrix([[-5.77350269e-01, -7.07106781e-01,  4.08248290e-01],
            [-5.77350269e-01,  9.95271580e-17, -8.16496581e-01],
            [-5.77350269e-01,  7.07106781e-01,  4.08248290e-01]]))


# 11 Introduction Quadractic Forms

---



## 1. Define the types of quadratic forms. 

A quadratic form $Q(x) = X^T \cdot A \cdot X$ (equivalently a symmetric matrix $A$) is

- a. Positive definite if $Q(x) > 0, \forall x \neq 0 ∈ R$;
- b. Negative definite if $Q(x) \geq 0, \forall x \neq 0 ∈ R$;
- c. Positive semi-definite if $Q(x) < 0, \forall x \neq 0 ∈ R$
- d. Negative semi-definite if $Q(x) \leq 0, \forall x \neq 0 ∈ R$
- e. Indefinite if $Q(x) > 0$ for some $x$ and  $Q(x) < 0$ for some other $x$.

## 2. There are several ways to find if a matrix is positive definite. What are they?

A matrix is to be positive defitinte if
- 1) all its eigenvalues are positive 
- 2) all determinants of its principal sub-matrices are positive

## 3. Indicate the type of definiteness of the following matrices.

### a. $\begin{bmatrix}9&-3\\-3&1 \end{bmatrix}$

$$det \begin{vmatrix} 9-\lambda&-3\\-3&1-\lambda \end{vmatrix} = (9-\lambda)(1-\lambda)-9=0\\
\lambda_{1}=10, \lambda_{2}=0$$

Therefore, the matrix is positive semi-definite.

### b. $\begin{bmatrix}-4&2&-1\\2&-4&2\\-1&2&-4 \end{bmatrix}$

$$det \begin{vmatrix} -4-\lambda&2&-1\\2&-4-\lambda&2\\-1&2&-4-\lambda \end{vmatrix} = -(4+\lambda)^3+4-4+4(4+\lambda)+4(4+\lambda)+(4+\lambda)=0\\
-(4+\lambda)^3+9(4+\lambda)=0\\
\lambda_{1}=-1.628, \lambda_{2}=-3, \lambda_{3}=-7.372$$

Therefore, the matrix is negative definite.

### c. $\begin{bmatrix}2&-1.5\\-1.5&3 \end{bmatrix}$


$$det \begin{vmatrix} 2-\lambda&-1.5\\-1.5&3-\lambda \end{vmatrix} = (2-\lambda)(3-\lambda)-2.25=0\\
\lambda_{1}=4.18, \lambda_{2}=0.99$$

Therefore, the matrix is positive definite.

### d. $\begin{bmatrix}4&2&-2\\2&4&2\\-2&2&4 \end{bmatrix}$

$$det \begin{vmatrix} 4-\lambda&2&2\\2&4-\lambda&2\\-2&2&4-\lambda \end{vmatrix} = (4-\lambda)^3-8+8-4(4-\lambda)-4(4-\lambda)+4(4-\lambda)=0\\
(4-\lambda)^3-4(4-\lambda)=0\\
\lambda_{1}=6, \lambda_{2}=0$$

Therefore, the matrix is positive semi-definite.



```python
print("lambda(a): \n", LA.eigvals(np.matrix([[9,-3],[-3,1]])))
print("lambda(b): \n", LA.eigvals(np.matrix([[-4,2,-1],[2,-4,2],[-1,2,-4]])))
print("lambda(c): \n", LA.eigvals(np.matrix([[2, -1.5],[-1.5,3]])))
print("lambda(d): \n", LA.eigvals(np.matrix([[4,2,-2],[2,4,2],[-2,2,4]])))
```

    lambda(a): 
     [10.  0.]
    lambda(b): 
     [-7.37228132 -3.         -1.62771868]
    lambda(c): 
     [0.91886117 4.08113883]
    lambda(d): 
     [ 6.0000000e+00 -4.4408921e-16  6.0000000e+00]

