Also known as the objective or cost function is the ***difference between the predicted output and actual target values***. Quantifies how well/poorly the model is performing. 

---
### Types of Loss Functions:

1. **Regression Loss Functions** (for continuous outputs):
    
    - **Mean Squared Error (MSE)**:
        
        MSE=1n∑i=1n(y^i−yi)2\text{MSE} = \frac{1}{n} \sum_{i=1}^n (\hat{y}_i - y_i)^2MSE=n1​i=1∑n​(y^​i​−yi​)2
        
        Penalizes larger errors more heavily. Used for regression tasks.
        
    - **Mean Absolute Error (MAE)**:
        
        MAE=1n∑i=1n∣y^i−yi∣\text{MAE} = \frac{1}{n} \sum_{i=1}^n |\hat{y}_i - y_i|MAE=n1​i=1∑n​∣y^​i​−yi​∣
        
        Measures the absolute difference. Less sensitive to outliers than MSE.
        
2. **Classification Loss Functions** (for discrete outputs):
    
    - **Cross-Entropy Loss** (Log Loss):
        
        Loss=−1n∑i=1n(yilog⁡(y^i)+(1−yi)log⁡(1−y^i))\text{Loss} = - \frac{1}{n} \sum_{i=1}^n \left( y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i) \right)Loss=−n1​i=1∑n​(yi​log(y^​i​)+(1−yi​)log(1−y^​i​))
        
        Commonly used in binary or multi-class classification problems. Measures the difference between predicted probabilities and actual class labels.
        
    - **Hinge Loss**: Used in Support Vector Machines (SVMs):
        
        Loss=max(0,1−yi⋅y^i)\text{Loss} = \text{max}(0, 1 - y_i \cdot \hat{y}_i)Loss=max(0,1−yi​⋅y^​i​)
3. **Custom Loss Functions**:
    
    - Designed for specific tasks, such as IoU (Intersection over Union) for object detection, perceptual loss for style transfer, etc.

---
### How It's Used:

1. **Backward Propagation**:
    - The loss is propagated backward through the network using a process called **backpropagation**.
    - The gradients of the loss with respect to the model parameters are computed.
2. **Optimizer**:
    - The optimizer (e.g., SGD, Adam) uses these gradients to update the model weights to minimize the loss.

### Example:

If you're training a neural network to predict house prices, you might use **MSE** as the loss function because you're predicting continuous values. If you're classifying images, **cross-entropy loss** would be more appropriate.

In summary, the loss function is central to training deep learning models, as it translates the model's performance into a numeric value that can be minimized to improve accuracy.