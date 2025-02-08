CS5720 Neural network and Deep learning,

CRN:-23848

Name:- Akula Tharun.

student ID:-700759411.

Home Assignment 1.

1.Tensor Manipulations & Reshaping

Clearer Output: The output now clearly labels each tensor and its rank/shape, making it easier to follow the transformations.

Transpose Explanation: The code now includes perm=[1, 0, 2] in tf.transpose. This is essential to correctly transpose from (2, 3, 4) to (3, 2, 4). The perm argument specifies the order of the new dimensions.

Broadcasting Explanation: The explanation of broadcasting is more detailed and accurate, covering the dimension alignment, compatibility rules, and the expansion process. It specifically addresses how the (1, 4) tensor is "stretched" to (3, 2, 4).

Implicit Broadcasting: The code demonstrates that broadcasting happens implicitly during the addition. You don't need a separate broadcasting function.

Error Handling Note: The explanation mentions that TensorFlow will raise an error if the shapes are not compatible for broadcasting, which is important for users to know.

2.Loss Functions & Hyperparameter Tuning

SparseCategoricalCrossentropy:tf.keras.losses.SparseCategoricalCrossentropy.This is the appropriate loss function when your y_true values are integer class labels (as in your example where y_true is [1, 0, 1, 1]).If your y_true was one-hot encoded,you would use CategoricalCrossentropy.It's very important to use the correct cross-entropy variant.

from_logits=False(Important):If your y_pred values are probabilities(like the example [0.8, 0.2, 0.9, 0.7]),you should not use from_logits=True.From_logits=True is only used when your model outputs raw logits (before a softmax activation).Since your predictions are probabilities,we set(or leave as default)from_logits=False.

Clearer Plotting:The plot now uses a grouped bar chart to clearly compare the loss values for the original and modified predictions.It's much easier to see the effect of the changes in predictions on the loss.

Integer y_true for CCE:The code now explicitly casts y_true to integers using tf.cast(y_true, tf.int32).This is crucial for SparseCategoricalCrossentropy to work correctly when your true labels are class indices.

NumPy Conversion: The .numpy() method is used to convert TensorFlow tensors to NumPy arrays for plotting with Matplotlib, which expects NumPy arrays.

3.Train a Model with Different Optimizers

Separate Examples:The code now has two distinct examples: one for binary classification and one for multi-class classification.This is much clearer and avoids the previous confusion.

Correct Loss Functions:
   Binary:For binary classification, tf.keras.losses.BinaryCrossentropy is used (and is the most appropriate loss).
   Multi-class:For multi-class classification with integer class labels, tf.keras.losses.SparseCategoricalCrossentropy is used.Critically,from_logits=False is set because the y_pred_multi_original contains probabilities(not logits).
   
from_logits=False:This is essential when your model predictions are probabilities(after a softmax or sigmoid activation).If your model outputs raw logits,then you would use from_logits=True.

Clearer Plotting:The plotting is now separated for the binary and multi-class examples,making it much easier to interpret.

Correct y_true for Multi-class:y_true_multi now correctly contains class indices(integers),which is what SparseCategoricalCrossentropy expects.

No More Modification of Predictions:I've removed the modification of predictions for simplicity.You can easily add that back in if you want to experiment with how changes in predictions affect the losses.The focus here is on using the correct loss functions.

4.Train a Neural Network and Log to TensorBoard

Log Directory:The log_dir is now dynamically generated using a timestamp.This ensures that each training run has its own separate log directory,preventing TensorBoard from getting confused.The logs are stored under the logs/fit/ directory.

TensorBoard Callback:The tf.keras.callbacks.TensorBoard callback is created,pointing to the log_dir.The histogram_freq=1 argument is added so that layer weights and activations histograms are also logged.This will add more information to the TensorBoard logs.

Training:The model.fit() method is called with the tensorboard_callback included in the callbacks list.This will automatically log the training data to the specified directory.

Launching TensorBoard:The code now prints clear instructions on how to launch TensorBoard.You must open a terminal or command prompt in the same directory as your Jupyter Notebook.Then,run the command:

