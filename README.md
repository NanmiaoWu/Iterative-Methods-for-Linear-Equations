## Iterative Methods

Suppose we plan to solve the linear equation 
![Ax=b](https://latex.codecogs.com/gif.latex?%5Cbg_black%20%5Cmathbf%7BA%7D%5Cmathbf%7Bx%7D%20%3D%20%5Cmathbf%7Bb%7D),
where A and b is known, which are n x n symmetric, positive-definite, and real matrix and n x 1 vector, respectively.

One solution is to utilize direct methods, which provide exact solution to the linear system, for example, Gaussian elimination. However, direct methods would incur huge compution costs when n is large. In this case, instead, we apply iterative methods to approximately solving it.

### Conjugate Gradient

We first introduce conjugate gradient method. Suppose that 

![conjugate vectors p](https://latex.codecogs.com/gif.latex?%5Cbg_white%20%5Cmathbf%7BP%7D%20%3D%20%5Cleft%20%5C%7B%20%5Cmathbf%7BP_%7B1%7D%7D%2C%20...%2C%20%5Cmathbf%7BP_%7Bn%7D%7D%20%5Cright%20%5C%7D),

where 

![what are conjugate vectors](https://latex.codecogs.com/gif.latex?%5Cbg_white%20%5Cmathbf%7BP_%7Bi%7D%7D%5E%7B%5Ctextup%7BT%7D%7D%5Cmathbf%7BA%7D%5Cmathbf%7BP_%7Bj%7D%7D%2C%20%5C%3B%5Cforall%20%5C%3B%5Cmathbf%7Bi%7D%20%5Cneq%20%5Cmathbf%7Bj%7D),

is a set of conjugate vectors with respect to matrix A. 

Let ![x*](https://latex.codecogs.com/gif.latex?%5Cbg_white%20%5Ctextbf%7Bx%7D%5E%7B*%7D) denote the solution. We can express it as

![x* expression](https://latex.codecogs.com/gif.latex?%5Cbg_white%20%5Ctextbf%7Bx%7D%5E%7B*%7D%20%3D%5Calpha_%7B1%7D%5Ctextbf%7BP%7D_%7B1%7D&plus;...&plus;%5Calpha_%7Bn%7D%5Ctextbf%7BP%7D_%7Bn%7D).

Therefore, we have

![x* second expressin](https://latex.codecogs.com/gif.latex?P_%7Bi%7D%5E%7BT%7DAx%5E%7B*%7D%20%3D%20P_%7Bi%7D%5E%7BT%7DA%5Cleft%20%28%20%5Calpha_%7B1%7DP_%7B1%7D&plus;...&plus;%5Calpha_%7Bn%7DP_%7Bn%7D%20%5Cright%20%29%20%3D%20%5Calpha_%7Bi%7DP_%7Bi%7D%5E%7BT%7DAP_%7Bi%7D).

Therefore, we have 

![alpha](https://latex.codecogs.com/gif.latex?%5Calpha_%7Bi%7D%20%3D%20%5Cfrac%7BP_%7Bi%7D%5E%7BT%7DAx%5E%7B*%7D%7D%7BP_%7Bi%7D%5E%7BT%7DAP_%7Bi%7D%7D%20%3D%20%5Cfrac%7BP_%7Bi%7D%5E%7BT%7Db%7D%7BP_%7Bi%7D%5E%7BT%7DAP_%7Bi%7D%7D),

which implies that we can get  ![alpha_i](https://latex.codecogs.com/gif.latex?%5Calpha_%7Bi%7D)  without knowing ![x*](https://latex.codecogs.com/gif.latex?x%5E%7B*%7D).

Substitute  ![alpha_i](https://latex.codecogs.com/gif.latex?%5Calpha_%7Bi%7D)  into ![x*](https://latex.codecogs.com/gif.latex?x%5E%7B*%7D), we have

![x* final expression](https://latex.codecogs.com/gif.latex?x%5E%7B*%7D%20%3D%20%5Csum_%7Bi%3D1%7D%5E%7Bn%7D%5Cfrac%7BP_%7Bi%7D%5E%7BT%7Db%7D%7BP_%7Bi%7D%5E%7BT%7DAP_%7Bi%7D%7DP_%7Bi%7D).



### Arnoldi Iteration

### Precondition Conjugate Gradient

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/NanmiaoWu/Iterative-Methods-for-Linear-Equations/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
