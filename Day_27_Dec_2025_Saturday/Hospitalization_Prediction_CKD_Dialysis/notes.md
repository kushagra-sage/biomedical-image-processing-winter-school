## Session: Hospitalisation predictive models in CKD for Dialysis patients

---

* **Speaker: Dr. Nikunj Kishor Rout**
* **Designation: Professor and Head of Department of Nephrology**
* **Organization: Kalinga Institute of Medical Sciences (KIMS), Bhubaneswar**

---

## 1.0 Introduction to Artificial Intelligence in a Medical Context

This session, led by Dr. Nikunj Kishor Rout, detailed the strategic integration of artificial intelligence into nephrology, framing it as a fundamental shift from reactive treatment based on established symptoms to proactive, predictive care. Dr. Rout explained that AI-driven tools are being designed not merely to mimic human cognition but to surpass human capacity for multi-variable data integration in real time, thereby enhancing clinical decision-making and improving patient outcomes in kidney disease management.

**1.1 Defining AI and Machine Learning**

Dr. Rout provided clear, functional definitions for the core technologies shaping this medical evolution:

* Artificial Intelligence (AI): Defined as a broad branch of science that enables machines to replicate fundamental human cognitive functions, allowing them to think, learn, and reason based on accumulated experience.
* Machine Learning (ML): Characterized as the most prevalent form of AI currently utilized in medical science. Dr. Rout explained that ML encompasses algorithms designed to learn directly from data and continually refine their performance as they are exposed to new information, without being explicitly reprogrammed.

**1.2 The Spectrum of AI Applications in Nephrology**

To illustrate the breadth of AI's impact, Dr. Rout outlined several key areas within nephrology where these technologies are already being applied successfully:

* Acute Kidney Injury (AKI): Developing models for the early prediction of AKI in various clinical settings.
* Medical Imaging: Analyzing images to detect malignant lesions or to measure total kidney volume in conditions like autosomal dominant polycystic kidney disease (ADPKD).
* Kidney Transplantation: Creating predictive models to forecast long-term transplant survival and outcomes.
* Chronic Kidney Disease (CKD): Building models that predict the rate of CKD progression in individual patients.
* Renal Pathology: Assisting in the analysis of kidney biopsy slides (histopathology) to identify various renal pathologies.
* Dialysis Care: Optimizing dialysis therapy parameters and developing strategies to reduce patient hospitalization rates.

This overview of current applications sets the stage for a deeper examination of a specific case study that demonstrates the profound potential of AI in a critical area of dialysis patient management.

---

## 2.0 Case Study: AI Model for Predicting Mortality in Hemodialysis Patients

Dr. Rout presented a compelling case study to demonstrate the transition from traditional, population-level statistical models to highly personalized, dynamic risk stratification enabled by AI. The study focused on predicting mortality in hemodialysis patients, showcasing how a machine learning framework provides superior predictive power in a high-stakes scenario where individualized clinical decisions are paramount.

**2.1 The Clinical Problem and Study Objective**

The study addressed the high mortality rate among hemodialysis patients, noted to be 3.8 to 9 times higher in Chinese cohorts—a figure likely comparable to the situation in India. Dr. Rout emphasized that traditional predictive tools like Cox regression analysis have proven insufficient for this task. Their moderate performance, with an Area Under the Receiver Operating Characteristic (AUROC) curve around 0.8, is inadequate for making critical clinical decisions with confidence, such as determining a patient's eligibility for kidney transplantation.

The study's primary objective was to build and validate a high-performance AI model capable of accurately predicting 1-year, 4-year, and 7-year mortality in this vulnerable patient population.

**2.2 Study Design and Methodology**

The research was conducted as a retrospective cohort study using data from Chinese medical centers. The design included:

* Training and Internal Validation: A cohort of nearly 5,900 patients from a large tertiary care hospital.
* External Validation: A separate cohort of 82 patients from another hospital to confirm the model's robustness and generalizability.

The study employed several machine learning techniques, including logistic regression, neural networks, support vector machines, and an Extreme Gradient Boosting (XGBoost) algorithm.

**2.3 Key Predictive Factors for Mortality**

The multivariate analysis identified five key factors independently associated with mortality in dialysis patients, forming the core inputs for the predictive algorithm:

1. Age: Positively correlated with an increased risk of mortality.
2. Ischemic Heart Disease: The presence of this comorbidity was a significant predictor of higher mortality.
3. Ejection Fraction: A lower ejection fraction, indicative of impaired cardiac contractility, was associated with worse survival.
4. Serum Albumin: Low levels, a marker for poor nutrition and inflammation, were negatively related to survival.
5. Neutrophils: Elevated counts, often indicating underlying infection or inflammation, were linked to higher mortality risk.

**2.4 Model Performance and Clinical Application**

The Extreme Gradient Boosting (XGBoost) model, referred to by the speaker as EGMB, demonstrated superior performance across all time points. The model’s robust predictive capabilities were validated both internally and externally.

Performance Metric	AUROC
1-Year Mortality Prediction	0.79
4-Year Mortality Prediction	0.933
7-Year Mortality Prediction	0.935
External Validation (Overall)	0.892

The success of this machine learning framework led to the development of a clinical online AI application. This clinical decision support tool operationalizes the XGBoost model by allowing clinicians to input a patient's values for the five key predictors (age, IHD status, ejection fraction, albumin, and neutrophils) to generate an immediate, personalized mortality risk score. This output guides crucial decisions, such as identifying low-risk patients who are favorable candidates for transplantation while helping to avoid the procedure in high-risk patients who would derive little benefit.

The proven success of this AI model serves as a powerful precedent for applying similar data-driven approaches to solve other pressing challenges in day-to-day dialysis care.

---

## 3.0 Proposed AI Applications for Improving Dialysis Patient Outcomes

Building on the case study, Dr. Rout outlined his roadmap for operationalizing AI at the bedside to directly address common, high-cost, and high-morbidity complications of dialysis care. This vision centers on shifting from retrospective analysis to real-time, personalized patient management to proactively prevent adverse events.

**3.1 Problem Area 1: Personalizing Fluid Management**

3.1.1 The Concept and Challenge of 'Dry Weight'

A cornerstone of euvolemic management in dialysis is determining a patient's 'dry weight': the lowest weight they can safely tolerate after fluid removal without symptoms of hypotension or dehydration. Dr. Rout explained that achieving this target is challenging because:

* It is dynamic and changes over time.
* Conventional assessment is subjective and relies on clinical signs with poor sensitivity for subclinical fluid imbalances.
* Inaccuracy leads to either chronic volume overload or dangerous episodes of hypotension during treatment.

3.1.2 AI-Powered Solutions for Fluid Management

Dr. Rout proposed an AI-powered framework to revolutionize fluid management by creating a holistic, dynamic patient profile.

* Integrated Data Inputs: An AI model would integrate multiple data streams, including pre- and post-dialysis blood pressure trends, bioimpedance spectroscopy data, ultrasound measurements of the vena cava, fluid overload biomarkers like NT-proBNP, and real-time dialysis machine data.
* Actionable Clinical Outputs: The algorithm could provide clinicians with a probability of fluid overload, suggest precise 'dry weight' adjustments, and generate a risk score for developing intradialytic hypotension.

3.1.3 Preventing Intradialytic Hypotension (IDH)

A critical application is the prevention of Intradialytic Hypotension (IDH), a common and dangerous complication. Dr. Rout noted that AI can predict IDH 30 to 60 minutes before its onset by analyzing real-time data inputs like the ultrafiltration rate and the slope of red blood cell volume.

* Actionable Outputs: The model can recommend reducing the ultrafiltration rate or extending the dialysis session time.
* Clinical Benefits: This proactive intervention can lead to fewer IDH episodes, reduced myocardial stunning, better long-term blood pressure control, and lower hospitalization rates.

**3.2 Problem Area 2: Predicting Hospitalization Risk**

3.2.1 The Rationale for an AI-Based Predictive Model

Patients with CKD are two to three times more likely to be hospitalized than the general population, and hemodialysis patients face an annual risk of 1.5 to 2 hospitalizations per patient per year. These events are primarily driven by volume overload, infections, and cardiovascular events. These drivers, such as the chronic volume overload and Intradialytic Hypotension (IDH) detailed previously, highlight the interconnected nature of dialysis complications and underscore the need for a holistic predictive model. Conventional risk scores are static and perform poorly at an individual level.

3.2.2 Proposed Study Framework

Dr. Rout outlined a framework for developing and validating an AI-based hospitalization prediction model:

* Primary Aim: To evaluate the effectiveness of AI models in forecasting hospitalization.
* Primary Objectives:
  * To develop a model that predicts the risk of unplanned hospitalization within 30 and 90 days.
  * To identify the key clinical and biological predictors that contribute most to hospitalization risk.
* Methodology:
  * Population: Patients with CKD stages 3-5 and those on dialysis.
  * Data Sources: Electronic medical records (EMRs), real-time dialysis machine data, and laboratory databases.
  * Potential Predictors: A wide range of variables, including demographics, lab values (albumin, hemoglobin), dialysis parameters, prior hospitalization history, and blood pressure variability.

3.2.3 Potential Key Predictors of Hospitalization

Dr. Rout suggested that such a study would likely identify several key predictors, including:

* Rapid interdialytic weight gain
* Low serum albumin levels
* Frequent episodes of intradialytic hypotension
* High C-reactive protein (CRP) levels

The overarching goal of these proposed applications is to harness AI for proactive, data-driven interventions that can significantly reduce patient morbidity and lower healthcare costs.

---

4.0 Conclusion

Dr. Rout's presentation powerfully articulated that artificial intelligence and machine learning are practical tools poised to transform nephrology. By enabling the creation of dynamic, personalized predictive models, these technologies can move clinical practice beyond static assessments toward real-time, proactive care. The ability to accurately forecast mortality, prevent acute complications like intradialytic hypotension, and predict hospitalizations offers a clear path to improving clinical decision-making and achieving superior outcomes for patients with kidney disease.
