# **Disaster Tweet Classification — DistilBERT Fine-Tuning Project**  
*A Machine Learning Project by David Ludemann*

---

##  **Project Overview**

This project explores the task of detecting whether a tweet refers to a real disaster, using the Kaggle “NLP-Getting-Started” dataset.

Two modeling approaches were implemented and compared:

1. **Logistic Regression with TF-IDF**  
2. **DistilBERT**, fine-tuned through multiple experimental runs (Runs 1–5)

The purpose of this work is to study how transformer fine-tuning behaves on small text datasets and to evaluate whether DistilBERT provides measurable improvements over classical machine learning baselines.

All steps—data download, preprocessing, training, evaluation, and model saving—run automatically from the provided script/notebook.

---

##  **DistilBERT Fine-Tuning (Runs 1–5 Summary)**

The project includes five progressively refined fine-tuning runs:

### **Run 1 — Baseline**
A straightforward fine-tune establishing the initial performance level.  
Training was stable but showed early fluctuations.

### **Run 2 — More Stable Optimization**
Lowering the learning rate and increasing gradient accumulation smoothed training and improved peak performance.

### **Run 3 — Longer Sequence Length + Label Smoothing**
Increasing max sequence length and adding label smoothing improved early generalization but introduced late-epoch degradation when smoothing was too high.

### **Run 4 — Tuned Regularization (Best Run)**
Reducing label smoothing and increasing warmup produced the strongest, most stable results.  
This run achieved the highest F1 score across all experiments.

### **Run 5 — Cosine Learning Rate Scheduling**
Cosine decay accelerated early improvement but plateaued before surpassing Run 4.  
This highlighted the importance of matching LR schedules to dataset size.

---

##  **Key Takeaways**

Fine-tuning DistilBERT on a small dataset is extremely sensitive to:

- learning rate  
- warmup ratio  
- sequence length  
- label smoothing  
- LR scheduling  

Each run provided incremental improvements and deeper insights into how transformers behave under different training conditions.  
Run 4 delivered the best overall balance of stability and accuracy.

---

##  **Comparison to Logistic Regression**

A Logistic Regression baseline was trained for contrast.  
While it achieved strong precision and is surprisingly competitive for short-text classification, it lacked the contextual depth of DistilBERT.

Logistic Regression tended to be conservative—catching fewer true disasters—while DistilBERT captured more nuanced patterns and achieved higher overall F1.

In summary:

- Logistic Regression: fast, simple, high precision  
- DistilBERT: better recall, better balance, better at understanding context  

DistilBERT ultimately outperformed the classical approach in overall classification quality.

---

##  **Conclusion**

This project demonstrates the value of transformer fine-tuning even on small datasets. Through a structured series of experiments, the model improved steadily, and the lessons learned highlight how critical training dynamics are for extracting the best performance from DistilBERT.

The final model (Run 4) achieved the strongest performance and represents the optimized configuration for this classification task.

---

