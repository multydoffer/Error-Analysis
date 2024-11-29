# Error-Analysis
Here we perform an error analysis on the Caduceus, ConvNova, and NTv2 models, focusing on the task of H3K14ac, where there is a noticeable performance gap: 70.71 vs. 60.84 vs. 57.22.

To analyze the errors, we select the sequences with significant performance differences and apply t-SNE for dimensionality reduction. We visualize the results from different angles to inspect if there are any evident patterns or distinctions between the errors made by the models.

![1732886634161](https://github.com/user-attachments/assets/226dc70e-5a61-4db5-ab4c-a0e79dc9c0d7)
![1732886668016](https://github.com/user-attachments/assets/8f8dbcee-5f06-4910-bb68-9560aacffce8)
![image](https://github.com/user-attachments/assets/4b8d3467-1181-45bc-87e8-07ee3a635f01)
![image](https://github.com/user-attachments/assets/fc6a7c90-bcc2-4789-9f82-4bc797dd2479)




From the visualizations, there doesn't seem to be a clear distinction between the errors made by Caduceus, ConvNova, and NTv2. To ensure rigor, we further train a linear SVM on the t-SNE reduced data to investigate if a hyperplane could reasonably separate the errors made by these models.

The SVM results are shown below. This outcome is close to randomly predicting between two classes (0 and 1), indicating that the error types between Caduceus and ConvNova do not differ significantly.


              precision    recall  f1-score   support

           0       0.55      0.51      0.53       600
           1       0.45      0.48      0.46       492

    accuracy                           0.50      1092
   macro avg       0.50      0.50      0.50      1092
weighted avg       0.50      0.50      0.50      1092

Similar results can be found in the following table, where 1 stands for error sequences from ConvNova and 0 for NTv2.

              precision    recall  f1-score   support

           0       0.56      0.52      0.54       749
           1       0.46      0.51      0.49       492

    accuracy                           0.51      1241
   macro avg       0.51      0.51      0.51      1241
weighted avg       0.52      0.51      0.51      1241

This analysis suggests that the error patterns in CNN, Transformer and SSM are not obvious.
