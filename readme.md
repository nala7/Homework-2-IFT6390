# Homework 2 - Practical component
#### IFT 6390 Fundamentals of Machine Learning 
##### Yorguin 
##### Nadia Gonzalez Fernandez


### Question 1

### Question 2

The derivative of the hinge loss term \( H \) with respect to \( w_k^j \) is given by the following steps. Having:

$$
H = \frac{1}{n} \sum_{(\mathbf{x}_i, y_i) \in S} \sum_{j' = 1}^{m} \mathcal{L}(\mathbf{w}^{j'}; (\mathbf{x}_i, y_i))
$$

we take the derivative with respect to \( w_k^j \):

$$
\frac{\partial H}{\partial w_k^j} = \frac{1}{n} \sum_{(\mathbf{x}_i, y_i) \in S} \sum_{j' = 1}^{m} \frac{\partial \mathcal{L}}{\partial w_k^j}
$$

Breaking down the derivative of \( \mathcal{L} \) by applying the chain rule:

1. Define the margin as:
   $$
   \text{margin}(\mathbf{w}^{j'}) = 2 - \langle \mathbf{w}^{j'}, \mathbf{x}_i \rangle \mathbf{1}\{y_i = j'\}
   $$

2. Express the loss function as:
   $$
   \mathcal{L}(\mathbf{w}^{j'}) = \max(0, \text{margin}(\mathbf{w}^{j'}))^2
   $$

Using the chain rule:
$$
\frac{\partial \mathcal{L}}{\partial w_k^j} = 2 \, \max(0, \text{margin}(\mathbf{w}^{j'})) \cdot \frac{\partial}{\partial w_k^j} \text{margin}(\mathbf{w}^{j'})
$$

Given that:
$$
\frac{\partial}{\partial w_k^j} \text{margin}(\mathbf{w}^{j'}) = -\mathbf{1}\{y_i = j\} \cdot x_{i,k}
$$

we obtain:
$$
\frac{\partial \mathcal{L}}{\partial w_k^j} = -2 \, \max(0, \text{margin}(\mathbf{w}^{j})) \, \mathbf{1}\{y_i = j\} \, x_{i,k} \, \text{step}(\text{margin}(\mathbf{w}^j))
$$

Thus, the derivative of the hinge loss term \( H \) with respect to \( w_k^j \) is:

$$
\frac{\partial H}{\partial w_k^j} = \frac{1}{n} \sum_{(\mathbf{x}_i, y_i) \in S} -2 \, \max(0, \text{margin}(\mathbf{w}^{j})) \, \mathbf{1}\{y_i = j\} \, x_{i,k} \, \text{step}(\text{margin}(\mathbf{w}^j))
$$
