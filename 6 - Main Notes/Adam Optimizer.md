2024-07-21 - 00:33
Status:
Tags: [[optimizer]] 
# Adam Optimizer

The Adam optimizer is an algorithm for gradient-based optimization of stochastic objective functions. It's widely used in machine learning and deep learning due to its efficiency and low memory requirements. Adam stands for **Adaptive Moment Estimation**.

Here are the key points about the Adam optimizer:

1. **Adaptive Learning Rate**: Adam combines the advantages of two other popular optimization algorithms: AdaGrad (which works well with sparse gradients) and RMSProp (which works well in on-line and non-stationary settings). By computing adaptive learning rates for each parameter, Adam improves the performance and convergence of the model.

2. **Momentum**: Like momentum in classical physics, the optimizer keeps track of an exponentially decaying average of past gradients (first moment) and the squares of the past gradients (second moment). This helps in accelerating the convergence of the optimizer.

3. **Parameter Update Rule**: The parameters of the model are updated based on the calculated first moment (mean of gradients) and second moment (uncentered variance of gradients), along with a small epsilon value to prevent division by zero.

The update equations are as follows:
$$m_t = \beta_1 m_{t-1} + (1 - \beta_1) g_t$$
$$
v_t = \beta_2 v_{t-1} + (1 - \beta_2) g_t^2
$$
$$\hat{m}_t = \frac{m_t}{1 - \beta_1^t}$$
$$\hat{v}t = \frac{v_t}{1 - \beta_2^t}$$
$$\theta_t = \theta_{t-1} - \frac{\alpha \hat{m}t}{\sqrt{\hat{v}_t} + \epsilon}
$$

Where:
- $m_t$  and $v_t$ are the first and second moment estimates.
- $beta_1$ and $beta_2$ are hyperparameters controlling the decay rates of these moment estimates (typically $beta_1 = 0.9$ and $beta_2 = 0.999$).
- $alpha$ is the learning rate.
- $epsilon$ is a small constant (e.g., $10^{-8}$) to avoid division by zero.
- $g_t$ is the gradient at time step $t$.
- $theta_t$  is the parameter at time step $t$.

Overall, Adam is popular because it requires little tuning of hyperparameters and works well in practice for a wide range of problems and architectures.

# Reference