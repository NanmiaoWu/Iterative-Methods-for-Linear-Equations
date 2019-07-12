## Iterative Methods

Suppose we plan to solve the linear equation 
![Ax=b](https://latex.codecogs.com/gif.latex?%5Cbg_black%20%5Cmathbf%7BA%7D%5Cmathbf%7Bx%7D%20%3D%20%5Cmathbf%7Bb%7D),
where A and b is known, which are n x n symmetric, positive-definite, and real matrix and n x 1 vector, respectively.

One solution is to utilize direct methods, which provide exact solution to the linear system, for example, Gaussian elimination. However, direct methods would incur huge compution costs when n is large. In this case, instead, we apply iterative methods to approximately solving it.

### Conjugate Gradient

We first introduce conjugate gradient method. Suppose that 

![conjugate vectors p](https://user-images.githubusercontent.com/29106484/61144125-a4012200-a499-11e9-94a2-1b7511091de8.png),

where 

![what are conjugate vectors](https://user-images.githubusercontent.com/29106484/61144273-140fa800-a49a-11e9-873c-0da839707a09.png),

is a set of conjugate vectors with respect to matrix A. 

Let ![x*](https://latex.codecogs.com/gif.latex?%5Cbg_white%20%5Ctextbf%7Bx%7D%5E%7B*%7D) denote the solution. We can express it as

![x* expression](https://user-images.githubusercontent.com/29106484/61144380-5933da00-a49a-11e9-9661-61f007c730fe.png).

Therefore, we have

![x* second expressin](https://user-images.githubusercontent.com/29106484/61144490-a021cf80-a49a-11e9-9cdc-1c7770f6ff0b.png).

Therefore, we have 

![alpha](https://user-images.githubusercontent.com/29106484/61144604-e37c3e00-a49a-11e9-8927-23b379fce2c9.png),

which implies that we can get  ![alpha_i](https://latex.codecogs.com/gif.latex?%5Calpha_%7Bi%7D)  without knowing ![x*](https://user-images.githubusercontent.com/29106484/61145178-62be4180-a49c-11e9-8fda-db6b4d99ebdd.png)
.

Substitute  ![alpha_i](https://latex.codecogs.com/gif.latex?%5Calpha_%7Bi%7D)  into ![x*](https://user-images.githubusercontent.com/29106484/61145178-62be4180-a49c-11e9-8fda-db6b4d99ebdd.png)
, we have

![x* final expression](https://user-images.githubusercontent.com/29106484/61144684-2b02ca00-a49b-11e9-9d1a-c49f910a1570.png).

Observing the above expression, we find that we do not need to calcaulate matrix inversion. Furthermore, the expression can be regarded as iterative process, wherein the nth term is added at the nth iteration.


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
