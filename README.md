# TensorFlow-Exercises
CS5720 Neural network and Deep learning

CRN:-23848

Name:- Akula Tharun

student ID:-700759411

Home Assignment 1

import tensorflow as tf


# 1.	Tensor Manipulations & Reshaping
**Clearer Output**: The output now clearly labels each tensor and its rank/shape, making it easier to follow the transformations.

**Transpose Explanation:** The code now includes perm=[1, 0, 2] in tf.transpose. This is essential to correctly transpose from (2, 3, 4) to (3, 2, 4). The perm argument specifies the order of the new dimensions.

**Broadcasting Explanation:** The explanation of broadcasting is more detailed and accurate, covering the dimension alignment, compatibility rules, and the expansion process. It specifically addresses how the (1, 4) tensor is "stretched" to (3, 2, 4).

**Implicit Broadcasting:** The code demonstrates that broadcasting happens implicitly during the addition. You don't need a separate broadcasting function.

**Error Handling Note:** The explanation mentions that TensorFlow will raise an error if the shapes are not compatible for broadcasting, which is important for users to know.
![alt text](./output/accuracy_5000images_15epochs.png?raw=true "Model accuracy with 5000 images")
