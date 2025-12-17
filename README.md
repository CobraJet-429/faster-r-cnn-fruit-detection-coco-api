## **Fruit Detection Using Faster R-CNN Evaluated with COCO Metrics**
Fine-tuned a Faster R-CNN (ResNet-50 + FPN) to detect apples, bananas, and oranges using a small object detection dataset. Training and evaluation follow TorchVision’s reference pipeline with COCO metrics (AP/AR) to assess detection accuracy and generalization on an untouched test set.

### **Task Objectives**

&nbsp;&nbsp;&nbsp;&nbsp;⚡ Split 20% of the 240 training data samples for validation (80:20 split)    
&nbsp;&nbsp;&nbsp;&nbsp;⚡ Keep the test set untouched until the final model evaluation     
&nbsp;&nbsp;&nbsp;&nbsp;⚡ Explore ground truth labels to identify class imbalances or other patterns     
&nbsp;&nbsp;&nbsp;&nbsp;⚡ Apply light data augmentation to improve generalization and reduce overfitting  
&nbsp;&nbsp;&nbsp;&nbsp;⚡ Use a Faster R-CNN model pretrained on ImageNet and COCO dataset  
&nbsp;&nbsp;&nbsp;&nbsp;⚡ Use TorchVision’s helper modules to interface cleanly with COCO API   
&nbsp;&nbsp;&nbsp;&nbsp;⚡ Monitor AP/AR metrics per epoch using validation data to track detection quality   
&nbsp;&nbsp;&nbsp;&nbsp;⚡ Run final inference and evaluation on the untouched test set 

### **Task Workflow**

&nbsp;&nbsp;&nbsp;&nbsp;✅ *Data Preparation*    
&nbsp;&nbsp;&nbsp;&nbsp;✅ *Model Training*    
&nbsp;&nbsp;&nbsp;&nbsp;✅ *Model Evaluation on Test Set*  

### **Dataset Information**

&nbsp;&nbsp;&nbsp;&nbsp;👨‍🚀 *Class Count:* 3  
&nbsp;&nbsp;&nbsp;&nbsp;👨‍🚀 *Official Train Size:* 240  
&nbsp;&nbsp;&nbsp;&nbsp;👨‍🚀 *Official Test Size:* 60  
&nbsp;&nbsp;&nbsp;&nbsp;👨‍🚀 *Image Resolution:* Varies, many high-res  
&nbsp;&nbsp;&nbsp;&nbsp;👨‍🚀 *Task:* Object detection of fruit objects    
&nbsp;&nbsp;&nbsp;&nbsp;👨‍🚀 *Source:* [Dataset Page on Kaggle](https://www.kaggle.com/datasets/mbkinaci/fruit-images-for-object-detection/data)  

### **Model Information**

&nbsp;&nbsp;&nbsp;&nbsp;🦖 *Model:* Faster R-CNN w. ResNet-50 + FPN   
&nbsp;&nbsp;&nbsp;&nbsp;🦖 *Parameters:* ~41M (including RPN + RoI heads)   
&nbsp;&nbsp;&nbsp;&nbsp;🦖 *Backbone Pretraining:* ResNet-50 pretained on ImageNet  
&nbsp;&nbsp;&nbsp;&nbsp;🦖 *Detector Pretraining:* Faster R-CNN pretrained on COCO  
&nbsp;&nbsp;&nbsp;&nbsp;🦖 *Recommended Input Res:* Variable resolution (auto-resizing)  
&nbsp;&nbsp;&nbsp;&nbsp;🦖 *Architecture:* ResNet-50 + FPN + RPN + RoI heads   
&nbsp;&nbsp;&nbsp;&nbsp;🦖 *Source:* [Paper](https://arxiv.org/pdf/1506.01497)

### **Results**

<img width="943" height="354" alt="image" src="https://github.com/user-attachments/assets/dee004fe-e569-4ba8-b72f-4a0e19d5748f" />

#### **Key Takeaways on Final Results**

- `mAP[0.50:0.95]` is consistent with training performance, suggesting the model generalizes well.
- AP and AR metrics being consistently high across large and medium object sizes (small are absent) and IoU thresholds indicate reliable predictions.
- `AP50` and `AP75` are also in line with training performance. 
- The test data also did not contain `small` objects with `0 < area < 1024 px^2`.
- This means`AP_small` and `AR_small` (flagged `-1.0`) did not contribute to the evaluation metrics.
- `AR10` and `AR100` are again identical and consistent with training performance.
