An algorithm used to adjust the [[parameters]] of a neural network in order to minimize the [[loss function]]. It guides the learning process by determining how the model should update its weights during training to improve its predictions.

### Key Functions of an Optimizer:

1. **Minimize Loss**:
    - Adjusts the model's parameters to reduce the difference between the predicted output and the actual target values.
2. **Leverages Gradients**:
    - Uses the gradients of the loss function with respect to the model parameters (computed through **backpropagation**) to decide the direction and magnitude of updates.

---

### Common Optimizers in Deep Learning:

1. **Gradient Descent**:
    
    - A basic optimization algorithm that updates the weights by moving them in the direction of the negative gradient of the loss function.
        
    - Update rule:
        
        w:=w−η⋅∇L(w)w := w - \eta \cdot \nabla L(w)w:=w−η⋅∇L(w)
        
        where:
        
        - www: weights
        - η\etaη: learning rate
        - ∇L(w)\nabla L(w)∇L(w): gradient of the loss function with respect to www.
    - Variants:
        
        - **Batch Gradient Descent**: Computes gradients using the entire dataset, which can be slow for large datasets.
        - **Stochastic Gradient Descent (SGD)**: Computes gradients for each training example, making it faster but noisier.
        - **Mini-Batch Gradient Descent**: Combines the benefits of batch and stochastic methods by computing gradients on small subsets (mini-batches) of the dataset.
2. **Momentum**:
    
    - Speeds up convergence by incorporating the concept of momentum, which accumulates past gradients to smooth updates.
    - Update rule: v:=β⋅v+∇L(w)v := \beta \cdot v + \nabla L(w)v:=β⋅v+∇L(w) w:=w−η⋅vw := w - \eta \cdot vw:=w−η⋅v where β\betaβ controls the contribution of past gradients.
3. **Adam (Adaptive Moment Estimation)**:
    
    - Combines ideas from momentum and adaptive learning rates to adjust the learning rate for each parameter individually.
        
    - Maintains moving averages of the gradient (mtm_tmt​) and the squared gradient (vtv_tvt​).
        
    - Update rule:
        
        w:=w−η⋅mtvt+ϵw := w - \eta \cdot \frac{m_t}{\sqrt{v_t} + \epsilon}w:=w−η⋅vt​​+ϵmt​​
        
        where ϵ\epsilonϵ prevents division by zero.
        
    - Widely used due to its efficiency and robustness.
        
4. **RMSprop (Root Mean Square Propagation)**:
    
    - Scales the learning rate based on the recent magnitude of gradients for each parameter.
    - Prevents oscillations and helps stabilize learning.
5. **Adagrad (Adaptive Gradient Algorithm)**:
    
    - Adjusts the learning rate for each parameter based on the historical gradients, giving larger updates for infrequent parameters and smaller updates for frequent ones.
6. **AdaDelta**:
    
    - An extension of Adagrad that addresses its diminishing learning rate problem.

---

### Key Parameters in Optimizers:

1. **Learning Rate (η\etaη)**:
    
    - Determines the step size for weight updates.
    - Too large: May overshoot the minimum.
    - Too small: Slow convergence.
2. **Momentum Coefficient (β\betaβ)**:
    
    - Controls the influence of past gradients.
3. **Other Hyperparameters**:
    
    - Optimizers like Adam have additional parameters (e.g., β1,β2\beta_1, \beta_2β1​,β2​, and ϵ\epsilonϵ) that need tuning.

---

### How Optimizers and Loss Functions Work Together:

- The loss function measures the model's error, and the optimizer decides how to reduce this error by updating the model parameters.
- For example:
    - Loss function calculates the error.
    - Gradients of the error are computed via backpropagation.
    - Optimizer updates the weights using these gradients.

---

### Summary:

An optimizer is a critical component in training neural networks, as it dictates how the model learns from data. Choosing the right optimizer and tuning its hyperparameters can significantly impact the model's performance and training efficiency.