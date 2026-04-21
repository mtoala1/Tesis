📌 Solar Panel Condition Classification using Deep Learning

This project evaluates deep learning and machine learning strategies for the automatic classification of surface conditions in photovoltaic (PV) modules using RGB images. The objective is to support automated monitoring and predictive maintenance in solar power plants.

Early detection of anomalies such as dirt, snow accumulation, and physical damage is essential to maintain energy yield and operational reliability, especially in large-scale or remote installations.

🧠 Models Evaluated

Four architectures were implemented and compared:

1️⃣ CNN trained from scratch

A custom Convolutional Neural Network composed of:

Multiple convolutional layers
MaxPooling layers
Dropout regularization
Fully connected layer with Softmax activation

This model serves as a baseline, as it does not rely on pretrained knowledge.

2️⃣ Transfer Learning – MobileNetV2 (Frozen Layers)

MobileNetV2 pretrained on ImageNet was used with:

Convolutional layers frozen
Custom dense classifier trained for PV anomaly detection

This approach leverages pretrained visual representations while limiting trainable parameters.

3️⃣ Transfer Learning – Partial Fine-Tuning

The last convolutional layers of MobileNetV2 were unfrozen to allow domain adaptation.
This configuration increases model capacity but may increase the risk of overfitting in limited datasets.

4️⃣ Hybrid Model – MobileNetV2 + SVM

A hybrid approach was implemented where:

MobileNetV2 (include_top=False) was used strictly as a feature extractor
All convolutional layers were frozen (trainable=False)
Deep features were extracted and fed into a Support Vector Machine (RBF kernel)

This decouples feature extraction from classification and improves stability in moderate-sized datasets.

🛠 Regularization Strategies

To mitigate overfitting in deep learning models, the following techniques were applied:

Data Augmentation (geometric and photometric transformations)
Dropout layers
Early Stopping based on validation loss
📊 Evaluation Metrics

Models were evaluated using:

Accuracy
Precision
Recall (Sensitivity)
F1-score (Macro & Weighted)
Confusion Matrix
ROC-AUC (Multiclass)
Precision-Recall Curves
📈 Results Summary
Transfer learning significantly outperformed the CNN trained from scratch.
Partial fine-tuning showed signs of overfitting due to dataset size limitations.
The Hybrid MobileNetV2 + SVM model achieved the best balance between stability and generalization:

Accuracy: 80%
F1-Macro: 0.81

The hybrid approach also improved detection performance for the critical "damage" class.

🚀 Practical Impact

The results demonstrate the feasibility of integrating computer vision systems into automated PV monitoring frameworks, enabling:

Reduced manual inspections
Improved fault detection
Predictive maintenance strategies
Reduced energy losses due to undetected anomalies
