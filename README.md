## Iterative Methods

Suppose we plan to solve the linear equation **Ax = b**,
where **A** is n x n symmetric, positive-definite, and real matrix, and **b** is n x 1 vector.

One solution is to utilize direct methods, which provide exact solution to the linear system, for example, Gaussian elimination. However, direct methods would incur huge compution costs when n is large. In this case, instead, we apply iterative methods to approximately solving it.

Note that all the following iterative algorithms have been implemented by [STE||AR Group
](https://github.com/STEllAR-GROUP) with the [Blaze library](https://bitbucket.org/blaze-lib/blaze/src/master/). Interested readers please refer to the [BlazeIterative](https://github.com/STEllAR-GROUP/BlazeIterative) for details.

### [Conjugate Gradient](https://github.com/NanmiaoWu/Iterative-Methods-for-Linear-Equations/blob/master/Conjugate%20Gradient.md) 

We first introduce conjugate gradient method. Before we introduce the iterative algorithms, let us look at the direct method, which enables us gain a better understanding of the iterative algorithms. 

#### Direct Method of Conjugate Gradient

Suppose that 

![conjugate vectors p](https://user-images.githubusercontent.com/29106484/61144125-a4012200-a499-11e9-94a2-1b7511091de8.png),

where 

![what are conjugate vectors](https://user-images.githubusercontent.com/29106484/61144273-140fa800-a49a-11e9-873c-0da839707a09.png),

is a set of conjugate vectors with respect to matrix A. 

Let ![x*](https://user-images.githubusercontent.com/29106484/61145178-62be4180-a49c-11e9-8fda-db6b4d99ebdd.png) denote the solution. We can express it as

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

Observing the above expression, we find that we do not need to calcaulate matrix inversion. Furthermore, the expression can be regarded as iterative process, wherein the n-th term is added at the n-th iteration.

#### Basic Iterative Method of Conjugate Gradient

As we mentioned above, the direct menthod is costly when n is large. To avoid such cost, we dynamic gererate the conjugate vectors instead of finding them via direct method.

Let ![x1](https://user-images.githubusercontent.com/29106484/61148338-27c00c00-a4a4-11e9-81dc-bf1ddb926b33.png) denote the initial guess, the update rule is shown as follow:

At k-th iteration:

![update rule](https://user-images.githubusercontent.com/29106484/61148860-568ab200-a4a5-11e9-9fa4-be12bbc9db0c.png)

where ![image](https://user-images.githubusercontent.com/29106484/61148953-918ce580-a4a5-11e9-801c-62e2734dbd04.png) is the redisual at the k-th iteration.

Then, after n-th iteration, we have ![image](https://user-images.githubusercontent.com/29106484/61160644-d6287900-a4c5-11e9-8247-e1b138aec760.png).

The proof is shown as follow:
First, we express ![image](https://user-images.githubusercontent.com/29106484/61149957-f0535e80-a4a7-11e9-94cd-de0cea69801f.png) as

![expression of xs](https://user-images.githubusercontent.com/29106484/61160320-a0cf5b80-a4c4-11e9-9fb6-e9351eee5be2.png).

Therefore, we have

![image](https://user-images.githubusercontent.com/29106484/61160613-ab3e2500-a4c5-11e9-8b7c-7ce87a6df824.png)


Therefore, we have

![image](https://user-images.githubusercontent.com/29106484/61160738-46cf9580-a4c6-11e9-9a64-3453c37abe20.png)

and we can express ![alpha_k](https://user-images.githubusercontent.com/29106484/61150457-188f8d00-a4a9-11e9-9456-f0b13b743838.png)
 as

![expression of alpha_k](https://user-images.githubusercontent.com/29106484/61150418-044b9000-a4a9-11e9-9602-aac99c67a0f5.png)

Also, we have

![image](https://user-images.githubusercontent.com/29106484/61151653-0c58ff00-a4ac-11e9-9df4-da8d60a4efe4.png)

Therefore, we have

![image](https://user-images.githubusercontent.com/29106484/61151743-44f8d880-a4ac-11e9-9431-441bf473ae31.png)

Finally, we can express ![alpha_k](https://user-images.githubusercontent.com/29106484/61150457-188f8d00-a4a9-11e9-9456-f0b13b743838.png) as

![image](https://user-images.githubusercontent.com/29106484/61151918-ac168d00-a4ac-11e9-9ba8-059c702278b9.png).


#### Improved Iterative Method of Conjugate Gradient

However, the above basic iterative method is still computationally expensive due to that it has to store all previous redisual vectors. A promising approach to avoid such cost is to generate a new conjugate vector by only using the previous one. Specifically, we determine the new conjugate vector by the following formular:

![image](https://user-images.githubusercontent.com/29106484/61161450-569ca900-a4c9-11e9-9778-8752fdabb34c.png)

where 

![image](https://user-images.githubusercontent.com/29106484/61161826-52718b00-a4cb-11e9-86a4-df2d4de6b4e2.png)

and

![beta_k](https://user-images.githubusercontent.com/29106484/61161555-e4789400-a4c9-11e9-8897-ff075b0da674.png).

Note that the proof of the above ![image](https://user-images.githubusercontent.com/29106484/61163774-f4967080-a4d5-11e9-9651-664ebe6ebe6e.png) expression is shown as follow:

Since ![image](https://user-images.githubusercontent.com/29106484/61163742-c7e25900-a4d5-11e9-871e-efc6479af677.png),

we have 

![image](https://user-images.githubusercontent.com/29106484/61163547-4d650980-a4d4-11e9-9b10-f5237d39cc42.png). 

Therefore, the numertor and denominator can be expressed as

![image](https://user-images.githubusercontent.com/29106484/61163638-e1cf6c00-a4d4-11e9-9aa3-38b640f2247e.png)

and

![image](https://user-images.githubusercontent.com/29106484/61163704-7b971900-a4d5-11e9-9a74-2ddb7e88806b.png),

respectively. Therefore, we can express ![image](https://user-images.githubusercontent.com/29106484/61163774-f4967080-a4d5-11e9-9651-664ebe6ebe6e.png) as the above.

Finally, the algorithm is shown as follow:
Let ![x1](https://user-images.githubusercontent.com/29106484/61148338-27c00c00-a4a4-11e9-81dc-bf1ddb926b33.png) denote the initial guess, ![image](https://user-images.githubusercontent.com/29106484/61161991-125ed800-a4cc-11e9-8b6a-7e0485e02552.png).

At k-th iteration:

![image](https://user-images.githubusercontent.com/29106484/61162762-d75ea380-a4cf-11e9-8f35-5131b75ce338.png)

### [Precondition Conjugate Gradient](https://github.com/NanmiaoWu/Iterative-Methods-for-Linear-Equations/blob/master/Precondition%20Conjugate%20Gradient.md) 

To better improve the convergence rate, we then introduce precondition conjugate gradient.

#### Precondition

The preconditioner **M** of matrix **A** is chosed such that matrix ![image](https://user-images.githubusercontent.com/29106484/61173498-d1150980-a559-11e9-9cb2-a865fdb0707b.png) has smaller condition number than matrix **A**. That is, the introducing of preconditioner can lead to the decrease of condition number, which finally results in the increase of the convergence rate. Then a question is raised, what is condition number?

#### Condition Number

Condition number is used to measure how the output changes when the input has a small change. For example, for linear equation 
**Ax = b**, if **b** has small change![image](https://user-images.githubusercontent.com/29106484/61173633-90b68b00-a55b-11e9-930a-547f7252d2e7.png), then **x** would have the change ![image](https://user-images.githubusercontent.com/29106484/61173648-afb51d00-a55b-11e9-8cf2-3bccd249908f.png), where ![image](https://user-images.githubusercontent.com/29106484/61173656-cd828200-a55b-11e9-8eb3-55f3e59f4300.png) are the error vectors.

Substitute ![image](https://user-images.githubusercontent.com/29106484/61173656-cd828200-a55b-11e9-8eb3-55f3e59f4300.png) into the linear equation, we have 

![image](https://user-images.githubusercontent.com/29106484/61173757-5bab3800-a55d-11e9-97a6-db6401919878.png)

Then our concern is: how a small change of ![image](https://user-images.githubusercontent.com/29106484/61173775-91502100-a55d-11e9-852f-d3a94e1ea4c5.png) would result in the change of ![image](https://user-images.githubusercontent.com/29106484/61173778-a0cf6a00-a55d-11e9-9f3d-2d07dbb8d8e3.png). Definitely, the smaller ![image](https://user-images.githubusercontent.com/29106484/61173778-a0cf6a00-a55d-11e9-9f3d-2d07dbb8d8e3.png) is better. 

Instead of looking the ![image](https://user-images.githubusercontent.com/29106484/61173775-91502100-a55d-11e9-852f-d3a94e1ea4c5.png) and ![image](https://user-images.githubusercontent.com/29106484/61173778-a0cf6a00-a55d-11e9-9f3d-2d07dbb8d8e3.png), let us look at the normalized version, that is, how a small change of ![image](https://user-images.githubusercontent.com/29106484/61173815-1d624880-a55e-11e9-93f5-f054890d15df.png) would lead to the change of ![image](https://user-images.githubusercontent.com/29106484/61173822-30751880-a55e-11e9-97d5-2d356825266c.png). Similarlly, it is better when ![image](https://user-images.githubusercontent.com/29106484/61173873-a5e0e900-a55e-11e9-9c2b-28b3ad11a3bf.png)
 is smaller. Then our goal is to find the upper bound of ![image](https://user-images.githubusercontent.com/29106484/61173873-a5e0e900-a55e-11e9-9c2b-28b3ad11a3bf.png).
 
Suppose ![image](https://user-images.githubusercontent.com/29106484/61173930-518a3900-a55f-11e9-8c3e-10c41c44eee5.png) is the eigenvalue of matrix **A**. Then we have ![image](https://user-images.githubusercontent.com/29106484/61173965-b3e33980-a55f-11e9-9c09-0adc0710b758.png), which implies that ![image](https://user-images.githubusercontent.com/29106484/61173972-cfe6db00-a55f-11e9-984b-e628eb1140b0.png). Similarly, we have ![image](https://user-images.githubusercontent.com/29106484/61173983-09b7e180-a560-11e9-8fb6-53017f0a56b1.png). Therefore, ![image](https://user-images.githubusercontent.com/29106484/61173992-2e13be00-a560-11e9-8f12-f5e56430463d.png).

Finally, the definition of condition number of **A** is: 

![image](https://user-images.githubusercontent.com/29106484/61178459-f97d2200-a5b2-11e9-950f-d002177750f4.png),

when matrix **A** is normal. **A** is said to be well-conditioned if the condition number is small. Furthermore, the definition of a general case is:

![image](https://user-images.githubusercontent.com/29106484/61178473-16195a00-a5b3-11e9-81b9-3d431bbf8b26.png).

#### Algorithm
After knowing the benefit of using preconditioner, let us focus on the algorithm part, which is from Wiki:

<img width="380" src="https://user-images.githubusercontent.com/29106484/61248052-f0f22c00-a717-11e9-94e8-3b0659595150.png">

#### Choices of Preconditioner
Then the last step is to choose a proper preconditioner. First we decompose matrix **A** as ![image](https://user-images.githubusercontent.com/29106484/61174340-56052080-a564-11e9-9647-48c9b51d609b.png), where **L** and **D** are strictly lower matrix and diagonal matrix, respectively. Next, we introduce some popular preconditioners in the following.

1. Jacobi preconditioning: 

**M = D**

2. Gauss-Seidel precondition: 

**M = L + D**

3. Successive over-relaxation (SOR) precondition: 

![image](https://user-images.githubusercontent.com/29106484/61174418-5a7e0900-a565-11e9-9438-7fe5894320e1.png), 

where ![image](https://user-images.githubusercontent.com/29106484/61174446-ae88ed80-a565-11e9-9639-aa646769f6d7.png) is the relaxation parameter.

4. Symmetric SOR preconditioning (SSOR): 

![image](https://user-images.githubusercontent.com/29106484/61174505-c745d300-a566-11e9-95dc-28a1888ed1f5.png)

5. Incomplete Cholesky factorization: 

![image](https://user-images.githubusercontent.com/29106484/61175824-8c9a6580-a57b-11e9-8d1c-03cb5904a9d6.png),

where matrix **K** can be computed as follow: first, we decompose matrix **A** as ![image](https://user-images.githubusercontent.com/29106484/61175770-97082f80-a57a-11e9-8d70-e8d0093ce92c.png) using Cholesky factorization, where ![image](https://user-images.githubusercontent.com/29106484/61175795-0e3dc380-a57b-11e9-8122-3b7ce6580d30.png) here is a lower triangular matrix. Next, we will compute a sparse lower triangular matrix **K**, which is close to **L**. Specifically, the elements, which are zeros in matrix **A**, are set to zeros in matrix **K**. 

### [Arnoldi](https://github.com/NanmiaoWu/Iterative-Methods-for-Linear-Equations/blob/master/Arnoldi.md) 


Arnoldi iteration is an iterative method to approximately find the eigenvalues and eigenvectors of matrices by generating an orthogonal basis of Krylov subspace. 

#### Krylov Subspace
Given a matrix **A** which is m x m, and an initial vector **b**, which is m x 1, we can construct the n-th order Krylov subspace:

![image](https://user-images.githubusercontent.com/29106484/61185593-d2f5d000-a620-11e9-8dde-e29f0db78fb0.png).

The advantage of constructing the Krylov subspace is that we can compute the matrix-vector product instead of cope with matrix **A** directly, which is particularly useful when **A** is large, since the cost of matrix-vector product is relatively cheaper.

Suppose ![image](https://user-images.githubusercontent.com/29106484/61185779-b9558800-a622-11e9-9412-a97c576c129f.png), where **H** and **Q** are m x m matrices, **H** is an upper Hessenberg matrix, which has zero entries below the first subdiagonal, and  **Q** is a unitary matrix with ![image](https://user-images.githubusercontent.com/29106484/61186005-8791f080-a625-11e9-8acb-f37c0a184472.png). With the aid of Krylov subspace, we can reduce the matrix **A** to an upper Hessenberg matrix. 

First, we can rewritten the expression of matrix **A** as **AQ = QH**, shown as follows:

![image](https://user-images.githubusercontent.com/29106484/61188119-34796700-a640-11e9-901f-ddf08f36dce2.png),

where n is the dimention of Krylov subspace as mentioned. Then we write a new expression of matrix **A**, which is part of the above equation, as ![image](https://user-images.githubusercontent.com/29106484/61188186-26781600-a641-11e9-9e90-1dffd1996170.png), where ![image](https://user-images.githubusercontent.com/29106484/61188198-43ace480-a641-11e9-98f5-7e0fd32f2f09.png) and 

![image](https://user-images.githubusercontent.com/29106484/61188176-05172a00-a641-11e9-94a6-560705a0619b.png).

Calculated the n-th columns of both sides, we have ![image](https://user-images.githubusercontent.com/29106484/61188268-49ef9080-a642-11e9-95bb-2411e1d2f0f4.png). Therefore, we can express  ![image](https://user-images.githubusercontent.com/29106484/61188294-bbc7da00-a642-11e9-82b8-47fb289e55a6.png) as

![image](https://user-images.githubusercontent.com/29106484/61188293-b074ae80-a642-11e9-9879-471aae3062f9.png),

which can be regarded as a iterative process.

#### Algorithm
The algorithm is shown as follow, which is from wiki:

<img width="360" alt="arnoldi" src="https://user-images.githubusercontent.com/29106484/61188359-7a83fa00-a643-11e9-84dd-237d41a29ecf.png">.

Note that ![image](https://user-images.githubusercontent.com/29106484/61189180-8a094000-a64f-11e9-9a4d-2cb2add138a7.png), which can be computed using the above algorithm. By removing the last row of matrix ![image](https://user-images.githubusercontent.com/29106484/61189338-99898880-a651-11e9-9ac7-53162e137e59.png), we have the n x n matrix ![image](https://user-images.githubusercontent.com/29106484/61189306-2c75f300-a651-11e9-9f52-93d045929020.png), which has the same eigenvalues as matrix **A**. That is how we reduce the matrix **A** to an upper Hessenberg matrix.


### Lanczos

Different from Arnoldi, here we suppose matrix **A** is an n x n Hermitian matrix and we plan to find the m most valueable eigenvalues. Let matrix **V** be an n x m matrix, which can be written as ![image](https://user-images.githubusercontent.com/29106484/61256376-3ae80b80-a732-11e9-9983-13fed202c8f7.png), where ![image](https://user-images.githubusercontent.com/29106484/61256466-81d60100-a732-11e9-82a7-e7e1b5862d95.png) are orthonormal Lanczos vectors. Let matrix **T** be a m x m tridiagonal real symmetric matrix with ![image](https://user-images.githubusercontent.com/29106484/61256853-037a5e80-a734-11e9-83c5-4d93c08ffaf6.png), which can be also written as

![image](https://user-images.githubusercontent.com/29106484/61256777-a1b9f480-a733-11e9-8f14-2ada201c7b02.png).

Note that ![image](https://user-images.githubusercontent.com/29106484/61256853-037a5e80-a734-11e9-83c5-4d93c08ffaf6.png) can be expressed as **AV = VT**. Comparing the j-th column of both sides, we have

![image](https://user-images.githubusercontent.com/29106484/61257040-e72af180-a734-11e9-8efb-91602ca90802.png). 

Furthermore, we have 

![image](https://user-images.githubusercontent.com/29106484/61257078-0e81be80-a735-11e9-92ee-bf14df8a64ab.png)

since ![image](https://user-images.githubusercontent.com/29106484/61257340-40475500-a736-11e9-97f2-a7772a4f9bb4.png).

In addition, we have

![image](https://user-images.githubusercontent.com/29106484/61257170-7df7ae00-a735-11e9-89cb-05cecb6fe48d.png) 

by multiplying ![image](https://user-images.githubusercontent.com/29106484/61257126-44bf3e00-a735-11e9-8fdb-5328125682d0.png) at both sides of ![image](https://user-images.githubusercontent.com/29106484/61257040-e72af180-a734-11e9-8efb-91602ca90802.png) since ![image](https://user-images.githubusercontent.com/29106484/61257206-a54e7b00-a735-11e9-905f-4b4b77a9d429.png), ![image](https://user-images.githubusercontent.com/29106484/61257210-aed7e300-a735-11e9-82d4-ba2b2dbb696a.png), and ![image](https://user-images.githubusercontent.com/29106484/61257217-b8614b00-a735-11e9-91a7-ac0053d59c6b.png) are orthogonal vectors.

However, in order to guarantee numerical stability, ![image](https://user-images.githubusercontent.com/29106484/61257446-a3d18280-a736-11e9-926c-20ab5c5383d1.png) and ![image](https://user-images.githubusercontent.com/29106484/61257458-adf38100-a736-11e9-9d50-2c31da4f44fb.png) should add additional terms. Therefore, they are expressed as follows:

1. ![image](https://user-images.githubusercontent.com/29106484/61257515-07f44680-a737-11e9-8791-19c3e4f04f3f.png),

since ![image](https://user-images.githubusercontent.com/29106484/61257210-aed7e300-a735-11e9-82d4-ba2b2dbb696a.png) and ![image](https://user-images.githubusercontent.com/29106484/61257217-b8614b00-a735-11e9-91a7-ac0053d59c6b.png) are orthogonal vectors.

2. ![image](https://user-images.githubusercontent.com/29106484/61257590-573a7700-a737-11e9-8e94-4389d4b0fde1.png)

since ![image](https://user-images.githubusercontent.com/29106484/61257206-a54e7b00-a735-11e9-905f-4b4b77a9d429.png) has unit norm.

The algorithm is shown as follow, which is from wiki:

<img width="792" alt="Lanczos" src="https://user-images.githubusercontent.com/29106484/61257752-fb242280-a737-11e9-9297-d238aabadb3b.png">
