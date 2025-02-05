# Detecting Anomalies In Network Traffic
1. Project Workflow
   - Loading the dataset
   - Preliminary data analysis
   - Exploratory data analysis
   - Distribution of the 'Outcome' variable
   - Normalization of continuous variables using StandardScaler and encoding of categorical variables using OneHotEncoder
   - Splitting the dataset into training and testing sets in an 80:20 ratio
   - Building an encoder neural network model with 4 dense layers (128, 64, 32, 8 neurons) and 20% dropout
   - Building the decoder as a mirror reflection of the encoder
   - The model was compiled using the RMSprop optimizer and binary crossentropy as the loss function
   - Visualization of model training progress
   - Calculation of reconstruction errors and visualization
   - Choosing the threshold
   - Confusion matrix and ROC curve
2. Conclusions
   - It was decided not to remove outliers, as they may represent potential network anomalies (e.g., DoS attacks), which are crucial for proper detection by the autoencoder. Removing these values could result in reduced effectiveness in identifying unusual patterns
   - Zero values (e.g., the number of bytes in transmission or the number of login attempts) can be crucial in the context of detecting specific types of attacks (e.g., attacks where a lack of activity may indicate a scanning attempt). Therefore, it was decided not to replace zero values with any other data to preserve the full interpretability of such cases
   - The training loss decreases rapidly during the first 10 epochs and then stabilizes
   - The validation loss is slightly higher than the training loss, but the difference is minimal, indicating good generalization
   - No overfitting was observed, thanks to the use of Dropout and the RMSprop optimizer
   - The normal data (both training and test sets) have very low reconstruction errors, indicating that the autoencoder has learned to effectively reconstruct typical network traffic
   - Anomalies generate higher reconstruction errors, which allows for effective differentiation from normal traffic
   - Raising the threshold from the 95th to the 98th percentile of reconstruction errors for normal data significantly reduced the number of false positives
   - AUC = 0.99 – A very good result, indicating high model effectiveness in separating normal cases from anomalous ones
   - The ROC curve is close to ideal, indicating a very high level of true positives with a low level of false positives
3. Screenshots
# Distribution of the 'Outcome' Variable
![Image](https://github.com/user-attachments/assets/d3520c2a-5174-40e4-9f5c-e0e80ff6e830)
# Correlation Map 
![Image](https://github.com/user-attachments/assets/4abc16c8-fd4f-4040-a777-dbebb2ef57b1)
# Boxplots with Outliers
![Image](https://github.com/user-attachments/assets/031d9e49-191c-495e-9b45-4c737d903d4e)
# Model Summary
![Image](https://github.com/user-attachments/assets/ec7b185f-0dd4-492c-a803-a559117fb6c9)
# Model Training Progress
![Image](https://github.com/user-attachments/assets/464c4b8d-c7e0-4418-807d-b1a0aa4f4cff)
# Distribution of Reconstruction Errors
![Image](https://github.com/user-attachments/assets/9de780f7-9dfe-4901-808d-a3edd82def6a)
# ROC Curve
![Image](https://github.com/user-attachments/assets/fa65c8ec-2b82-4aa9-8e6f-23d493edd05d)
