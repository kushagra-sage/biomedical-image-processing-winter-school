##  Session Details : Deep Learning for Biomedical Signals and Medical Imaging: From Clinical Time Series to Image-Based Decision Support

* **Speaker:** Dr. Paola Barra
* **Designation:** Specialist in Computer Vision, Machine Learning, and Biometric Systems
* **Organization:** Parthenope University of Naples, Italy
* **Topic:** Application of practical deep learning methods for biomedical data analysis with a focus on **trust**, **robustness**, and **explainability**

---

## 1.0 Introduction: The Critical Role of Trust in Medical AI

The development of Artificial Intelligence (AI) for clinical settings represents a strategic imperative in modern healthcare. As highlighted by Dr. Paola Barra, clinical environments are characterized by increasingly complex data, from hundreds of MRI slices to long physiological recordings, where decisions must often be made quickly with incomplete information.

In this high-stakes context, the primary challenge for AI adoption is not merely achieving high accuracy but building a foundational sense of trust among clinicians and patients. An AI model with 90% accuracy on paper is effectively worthless if clinicians do not trust it enough to use it. This reality shifts the focus from pure performance to the development of systems that are robust, transparent, and ethically aligned. Consequently, any discussion of medical AI must begin with the foundational principles that make these powerful systems truly trustworthy.

---

## 2.0 Foundational Principles for High-Risk AI Systems

Before exploring specific applications, Dr. Barra established a clear framework for developing AI in high-stakes environments like healthcare. This framework is built on a set of core principles that extend far beyond simple performance metrics, addressing the unique demands of clinical practice where the consequences of error are profound. These principles serve as the bedrock for designing and deploying AI systems that are not only effective but also safe, reliable, and accountable. The following subsections detail these core requirements for trustworthy clinical AI.

---

## 2.1 The Asymmetry of Errors and the Question of Trust

Dr. Barra presented a critical argument regarding the asymmetry of errors in medical AI, emphasizing that not all mistakes carry the same weight. The clinical cost of a false negative—such as a missed cancer or a missed arrhythmia—is dramatically different from that of a false positive, which might lead to extra tests and patient anxiety. This imbalance changes everything, from model selection to how results are communicated. Accuracy on paper becomes a secondary concern if the system is not trusted in practice. Dr. Barra framed this fundamental challenge with a direct question that cuts to the heart of the issue:

> “The AI says don't hospitalize, would you trust it?”

This illustrates that trust is not an abstract concept but a practical prerequisite for any AI tool to have a meaningful impact in a clinical setting.

---

## 2.2 The Three Pillars of Trustworthy AI

Dr. Barra outlined three essential pillars for any AI system intended for use in high-risk domains like medicine. These pillars provide a comprehensive framework for responsible development and deployment.

* **Lawful:** The system must comply with all relevant regulations, such as the GDPR and the AI Act.
* **Ethical:** The system must not discriminate or perpetuate biases in its classification that could systematically harm vulnerable patient groups.
* **Robust:** The system must not break down when data changes slightly; it must be resistant to noise and measurement errors and remain safe under imperfect, real-world conditions.

---

## 2.3 The Role of Explainable AI (XAI)

Explainable AI (XAI) is essential for building trust across the entire healthcare ecosystem, including clinicians, patients, data scientists, and regulators. Dr. Barra explained that XAI provides the transparency needed to understand how a model arrives at a recommendation, which is crucial for validating its clinical plausibility. By making the AI's reasoning accessible, XAI supports human oversight and enables safe human-AI collaboration. This moves the conversation from simply accepting a model's output to critically evaluating its evidence, allowing clinicians to maintain control and make informed judgments.

---

## 2.4 The Human-in-the-Loop Workflow

Dr. Barra presented a stable and remarkably consistent workflow for implementing clinical AI. This process underscores the central role of human oversight at every stage.

1. Data: Begin with clinically relevant data.
2. Preprocessing: Decide on preprocessing steps that are clinically acceptable and preserve important information.
3. Model Training: Train a model on the prepared data.
4. Evaluation: Evaluate the model using clinically meaningful metrics that reflect real-world priorities.
5. Human Decision: Connect the model's output directly to a human decision-maker.

He stressed that explainability and the "human in the loop" are not optional add-ons; they are the core interface between the algorithm and the clinical workflow. This principle of augmenting, rather than replacing, human expertise is demonstrated in the first case study.

---

## 3.0 Case Study 1: Gaze Support in Radiology for Multiple Sclerosis Diagnosis

This first case study demonstrates the principle of supporting human judgment rather than attempting to replace it. The clinical context is the radiological analysis of MRI scans for Multiple Sclerosis (MS), a task that is visually demanding and can lead to significant cognitive fatigue for human experts. The proposed solution, Focus Gaze DX, is designed to act as a "quiet companion" that helps radiologists maintain focus and reduce errors without dictating a diagnosis.

---

## 3.1 The Clinical Challenge

Diagnosing MS from MRI scans places an immense cognitive load on radiologists. They must meticulously analyze hundreds of image slices under significant time pressure, looking for subtle lesions that can be small or ambiguous. Studies report retrospective error rates in radiology of around 30%, with daily practice error rates between 3% and 5%. These errors often stem not from a lack of skill but from perceptual misses driven by systemic factors like fatigue and cognitive overload, especially during long sessions or overnight shifts.

---

## 3.2 The Proposed Solution: Focus Gaze DX

The core concept of Focus Gaze DX is to leverage eye-tracking and reinforcement learning to model the gaze patterns of expert radiologists. The system learns what constitutes a thorough visual search and can detect in real time if a clinician has underexplored a potentially significant region of an MRI scan. When an underexplored area is identified, the system provides subtle, non-intrusive visual feedback, such as a colored contour, that gently prompts the radiologist to take a second look. It provides this feedback without alarms or interruptions, functioning as a quiet companion that helps to keep attention where it is needed.

---

## 3.3 The Goal: Supporting Attention, Not Dictating Diagnosis

The primary objective of this approach is to support and enhance human expertise, making the diagnostic process safer and more consistent. Dr. Barra repeatedly emphasized that the mission is not to replace the radiologist but to provide a tool that keeps the human firmly in control. By reducing blind spots and mitigating the risk of fatigue-driven failures, the system empowers clinicians to perform at their best. This focus on augmenting human attention provides a clear model for responsible AI integration, a theme that carries into the next case study addressing a different imaging challenge.

---

## 4.0 Case Study 2: Evolving Neural Networks for Melanoma Detection

This second case study on melanoma classification tackles the critical issue of model robustness. It addresses the common and dangerous problem of "domain shift," where an AI model's performance degrades significantly when applied to new data from a different source, device, or patient population. Dr. Barra’s team explored a novel approach that uses a genetic algorithm to automatically design a more robust AI architecture.

---

## 4.1 The Clinical Challenge

Diagnosing melanoma from dermoscopic images is difficult due to the visual similarity between benign and malignant lesions and significant variability in image quality. Dr. Barra highlighted the danger of models that are not robust by citing a powerful example from the ISIC challenge: a winning algorithm from 2018 with 88.5% accuracy saw its performance plummet to 63.6% on the 2019 dataset. This dramatic drop was not due to a flawed model but to a more realistic clinical scenario with greater data variability, illustrating that high accuracy on a single dataset is not a guarantee of real-world reliability.

---

## 4.2 The Proposed Solution: A Genetic Algorithm for CNN Design

To build a more robust model, the proposed method automates the search for an optimal Convolutional Neural Network (CNN) architecture using a genetic algorithm. Dr. Barra used the analogy of treating the network design as a "genome," where its components—such as layers and hyperparameters—are "genes." These "genomes" evolve over generations based on a fitness criterion, which is typically classification accuracy. This evolutionary approach allows the system to discover effective architectures without relying on human intuition or manual design.

---

## 4.3 The Rationale and Process

The logic behind this automated approach is to reduce manual bias in architecture design and enable a more systematic and expansive search of possible solutions. The evolutionary process involves stages analogous to natural selection: top-performing architectures ("individuals") are selected to "reproduce" through crossover and mutation, creating new generations of models. Over time, only the fittest architectures survive, leading to a highly optimized model for the specific task.

However, Dr. Barra emphasized that this method comes with critical real-world trade-offs. Automated architectural search is computationally expensive and not a default choice; it trades computing resources for a potentially more robust design. Furthermore, she warned that such algorithms carry the risk of overfitting the validation protocol if the protocol is weak, or optimizing for the wrong objective if the goal is not perfectly aligned with clinical priorities. This practical engineering context is crucial for determining when such an advanced approach is truly warranted.

---


## 5.0 Case Study 3: Detecting Premature Ventricular Contractions (PVCs) in ECG Signals

This final case study shifts the focus from static images to continuous time-series data in the form of electrocardiogram (ECG) signals. The clinical problem is the detection of Premature Ventricular Contractions (PVCs), which are irregular heartbeats that can be intermittent and may signal underlying heart disease. Although the data modality is different, the core principles of using AI for decision support and ensuring model interpretability remain central to the approach.

---

## 5.1 The Clinical Challenge

Detecting PVCs is medically important, as cardiovascular diseases are the leading cause of death worldwide, accounting for an estimated 32% of all deaths. The challenge lies in accurately identifying these anomalies from complex and often noisy ECG signals. This involves not only detecting the presence of a PVC but also classifying its severity and understanding its specific morphological pattern, as some PVCs are harmless while others can indicate life-threatening conditions.

---

## 5.2 Approach A: Image-Based Clustering (Experimental)

As an initial exploratory step, Dr. Barra's team experimented with converting one-dimensional ECG waveforms into two-dimensional binary images. They then used distance matrices and K-means clustering to analyze these images, aiming to discover if consistent latent patterns existed within different types of heartbeats. While this approach revealed promising structures in the data, it was primarily an experimental step to confirm the presence of classifiable patterns.

---

## 5.3 Approach B: RNN-Based Anomaly Detection

The second, more advanced approach was based on a powerful hypothesis: a Recurrent Neural Network (RNN) trained only on healthy heartbeats should become an expert at predicting normal cardiac patterns. Consequently, when this model encounters an unhealthy heartbeat (a PVC), it will fail to predict the pattern accurately. This prediction error, quantified by the Root Mean Squared Error (RMSE), can then be used as a reliable signal for anomaly detection. In line with their previous work, the team again used a genetic algorithm to automatically design the optimal RNN architecture for this task.

---

## 5.4 From Detection to Explainability

This anomaly detection approach connects directly to explainability. Dr. Barra explained that by identifying where in the ECG signal the prediction error is highest, the model can automatically localize the anomaly. This provides clinicians with highly interpretable evidence, pointing to the specific segment of the heartbeat that is abnormal. For instance, Dr. Barra shared that her team's preliminary results suggest that PVC patterns tend to concentrate in specific regions of the cardiac cycle, specifically between positions 22-27 and 37-44. Instead of just a binary label ("PVC" or "Not PVC"), the system provides actionable, reviewable information that a clinician can use to validate the finding. To this end, Dr. Barra concluded with a call for collaboration, stating that the team is actively seeking physicians and cardiologists to help validate these important findings.

---

## 6.0 The Explainable AI (XAI) Landscape in Healthcare

To synthesize the principles demonstrated in the case studies, Dr. Barra presented a conceptual map for categorizing different XAI methodologies. This framework helps stakeholders choose the right strategy for a given clinical use case, ensuring that the chosen approach aligns with the specific need for transparency and trust.

---

## 6.1 White-Box vs. Black-Box Models

First, a distinction is made between "White-Box" and "Black-Box" models. White-box models, such as logistic regression or small decision trees, are inherently transparent. Their decision-making processes are simple, easy to validate, and straightforward to communicate, making them a preferred choice when interpretability is the paramount concern.

In contrast, "Black-Box" models such as deep neural networks, offer superior predictive power at the cost of transparency. Their internal workings are opaque, which creates significant challenges for building trust and achieving regulatory approval in clinical environments. While highly accurate, their inability to explain their reasoning is a major barrier to adoption.

---

## 6.2 Global vs. Local Explanations

Second, explanation methods can be categorized as either global or local. "Global" explanation methods aim to describe a model's overall behavior, answering questions like "Which features are most important across all predictions?" These methods are useful for auditing, general validation, and communicating a model's logic to institutions.

"Local" explanation methods, such as LIME and SHAP, focus on explaining a single, individual prediction. They answer the question, "Why was this specific patient classified this way?" Dr. Barra noted that local explanations are particularly valuable at the bedside, as they directly support clinical decision-making, patient communication, and the shared responsibility between the clinician and the AI.

---

## 7.0 Conclusion: A Vision for Human-Centered Clinical AI

Dr. Barra's presentation delivered a clear and compelling vision for the future of clinical AI. Her core thesis is that the goal should never be to replace clinicians but to support human expertise in a safe, transparent, and responsible manner. Whether analyzing medical images or physiological signals, the fundamental requirements remain the same. Trust, human-in-the-loop systems, robustness against real-world data shifts, and deep explainability are not optional features but non-negotiable prerequisites for any AI system to achieve meaningful and positive clinical impact. This human-centered approach is essential for designing AI systems that can finally be integrated successfully and responsibly into the practice of medicine.

---
