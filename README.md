# Error-Analysis
Here we perform an error analysis on the Caduceus, ConvNova, and NTv2 models, focusing on the task of H3K14ac, where there is a noticeable performance gap: 70.71 vs. 60.84 vs. 57.22.

To analyze the errors, we select the sequences with significant performance differences and apply t-SNE for dimensionality reduction. We visualize the results from different angles to inspect if there are any evident patterns or distinctions between the errors made by the models.

![image](https://github.com/user-attachments/assets/a884baa3-82da-4aa0-9faa-5bb0b9014f2b)
![image](https://github.com/user-attachments/assets/27089197-a1fd-45fd-b82c-2a6ce4d74f6c)
![image](https://github.com/user-attachments/assets/f2084317-13df-4121-b3ee-7932c9681da9)
![image](https://github.com/user-attachments/assets/fc6a7c90-bcc2-4789-9f82-4bc797dd2479)
![image](https://github.com/user-attachments/assets/b57fd33b-7bca-4d07-8cdd-3f312d7b0e88)




From the visualizations, there doesn't seem to be a clear distinction between the errors made by Caduceus, ConvNova, and NTv2. To ensure rigor, we further train a linear SVM on the t-SNE reduced data to investigate if a hyperplane could reasonably separate the errors made by these models.

The SVM results are shown below. This outcome is close to randomly predicting between two classes (0 and 1), indicating that the error types between Caduceus and ConvNova do not differ significantly.


              precision    recall  f1-score   support

           0       0.55      0.51      0.53       600
           1       0.45      0.48      0.46       492


Similar results can be found in the following table, where 1 stands for error sequences from ConvNova and 0 for NTv2.

              precision    recall  f1-score   support

           0       0.56      0.52      0.54       600
           1       0.46      0.51      0.49       443

This analysis suggests that the error patterns in CNN, Transformer and SSM are not obvious.
