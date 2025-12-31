## * Session: AI-driven ROI detection

---

* **Speaker:**  Dr. Sulagna Mohapatra
* **Designation:** AI & Automation Strategic Architect
* **Organization:** Volktek Corporation, Taiwan
  
---

## 1.0 Introduction to AI-driven ROI Detection

The ability to automatically identify specific regions of interest (ROI) in images represents a significant leap forward from traditional, manual image processing techniques. Where older methods relied on pre-defined rules for tasks like skull removal or noise reduction, modern Artificial Intelligence (AI) offers an intelligent, data-driven approach to directly detect and localize objects. This session provides a comprehensive overview of this evolution, exploring the journey from foundational image classification to advanced, direct object detection.

Dr. Sulagna N. began by differentiating between the foundational role of image pre-processing and the more sophisticated capabilities of AI-driven object detection. While both can be used for ROI analysis, the AI approach allows a system to learn complex patterns and identify objects with a high degree of accuracy and automation. The stated goal for the session was to first revisit the core AI concepts of classification (identifying if an object is present) and localization (identifying where an object is) through a detailed case study. This foundational review serves as a stepping stone to understanding the primary topic: direct object detection, where an AI model accomplishes both tasks simultaneously. The following in-depth analysis of ischemic stroke detection provides a practical application of these initial concepts.

---

## 2.0 In-Depth Case Study: Ischemic Stroke Image Analysis

This case study, drawn from the speaker's own doctoral research, serves as a foundational example illustrating the entire AI development pipeline. It chronicles a real-world project, from understanding a complex clinical problem to building, validating, and preparing a model for deployment. By walking through this process, the session demonstrates the practical challenges and innovative solutions involved in creating a clinically useful AI tool.

**2.1 The Clinical Problem and Motivation**

An ischemic stroke occurs when blood flow to the brain is obstructed, depriving brain tissue of oxygen and causing it to die. Early and accurate diagnosis is critical for patient outcomes, as prompt treatment can save threatened but still viable brain tissue in the surrounding area, known as the penumbra.

Clinicians face significant challenges in achieving this early diagnosis. In emergency settings, non-contrast CT (NCCT) scans are the imaging method of choice because they are widely available, affordable, and avoid the potential side effects of contrast agents. However, within the critical first 12 hours, the signs of an ischemic stroke on an NCCT scan are often invisible to the naked eye, even for experienced radiologists.

This diagnostic gap provided several key clinical motivations for developing an AI solution:

* Low Visibility: The difficulty in visually distinguishing early-stage stroke-affected tissue from normal brain tissue on NCCT scans.
* Time-Consuming Workflow: The need for radiologists to manually review dozens of individual CT slices for each patient, a process that is both laborious and prone to error under time pressure.
* Diagnostic Complexity: The challenge of differentiating a new, acute stroke from an old, pre-existing infraction, which can appear similar and confound diagnosis.
* Tooling Limitations: The inaccuracies and limitations of existing software tools and manual scoring systems used to quantify stroke severity.

**2.2 The Technical AI Challenges**

Beyond the clinical hurdles, AI developers encountered several technical problems when working with this medical data:

1. Pixel and Intensity Variation: Images produced by scanners from different vendors (e.g., Philips, Siemens) exhibit significant variations in pixel intensity, creating a major challenge for building a model that can perform consistently across data from different sources.
2. Image Rotation and Alignment: Patients, especially in emergency situations, may not be perfectly positioned in the scanner, resulting in head rotations and alignment issues that make it difficult to standardize the images for analysis.
3. Presence of False Positives: The brain contains numerous structures, such as the highly attenuated (bright) skull or large arteries, that can be mistaken for strokes by an AI model, leading to false-positive detections.
4. Non-uniformity of Strokes: Ischemic strokes have no predictable shape, size, or location within the brain, making it difficult to create a generalized model that can reliably detect them.

**2.3 Method 1: Classification ("Is a Stroke Present?")**

The first approach was to build a classification model to answer a simple but critical question: is this patient "normal" or do they have an "ischemic stroke"? This involved a meticulous data preparation and model development workflow.

The data pre-processing pipeline included the following steps:

1. Data Conversion: 3D DICOM files from the scanner were converted into a series of 2D JPG images, a format more suitable for the 2D CNN models available at the time.
2. Ground Truth Labeling: A novel method was developed to create accurate labels. Since strokes were not visible on the NCCT scans, the team cross-referenced them with corresponding MRI scans of the same patient, where strokes are clearly visible. This novel cross-modality labeling strategy was a direct solution to the core clinical challenge: the invisibility of early-stage strokes on the very NCCT images the model needed to learn from.
3. Skull Removal: Standard image processing techniques—including binary thresholding, morphological operations (erosion and opening), and masking—were combined to isolate the brain tissue from the bright, confounding skull.
4. Noise Removal & Cropping: Finally, algorithms were applied to remove noise from the images and crop them to the relevant brain tissue area, eliminating unnecessary background information.

For model development, the team selected the VGG16 architecture. The team customized the VGG16 architecture through data augmentation techniques (rescaling, flipping, zooming) and hyperparameter tuning. Key modifications included altering the final dense layer and utilizing the Adam optimizer. The model's robustness was validated using a 10-fold cross-validation methodology. The resulting proof-of-concept software demonstrated an end-to-end pipeline capable of taking raw NCCT images, automatically pre-processing them, and outputting a final classification of "normal" or "ischemic," helpfully providing the slice numbers most likely to contain the stroke. This approach achieved an impressive classification accuracy of approximately 83%, a significant result given the difficulty of analyzing non-contrast CT images.

**2.4 Method 2: Classification plus Localization ("Where is the Stroke?")**

The next goal was to not only classify the patient but also pinpoint the exact location of the stroke. The primary challenge was again ground truth generation; since the stroke was invisible on the NCCT scans, a method was needed to tell the model where to look. The solution involved superimposing the stroke regions, identified from clear MRI scans, onto the corresponding NCCT images to create annotated training data.

To train the model, the team developed an innovative patch-based approach. To prevent the model from "cheating" by simply learning the colored annotation border, the team developed a novel training strategy. The model was trained not on the colored patches, but on the corresponding unlabeled patches from the stroke hemisphere, which it learned to differentiate from normal patches taken from the healthy, opposite hemisphere of the same patient's brain.

During testing, the trained model analyzes patches from a new patient's CT scan, classifies them as normal or abnormal, and then uses a template matching algorithm to map the abnormal patches back onto the full brain slice, effectively localizing the stroke. While effective, this patch-based method had critical limitations, including its time-consuming nature and a significant data bias problem when stroke regions were small, leading to a class imbalance between abnormal and normal patches.

---

## 3.0 Advancing to Direct Object Detection

The strategic shift from the multi-step, patch-based localization method to a direct object detection approach was driven by the need for a solution that was not only more efficient but also less susceptible to the data bias issues inherent in the patch method. Instead of first classifying and then localizing, an object detection model performs both tasks in a single pass. The core output of this type of model is a bounding box—a rectangle drawn precisely around the object of interest, along with a class label.

**3.1 One-Stage vs. Two-Stage Detectors** 

Object detection models are broadly categorized into two types, each with its own trade-offs:

Detector Type	Key Characteristics
One-Stage Detector	Fast and suitable for real-time applications (e.g., YOLO, RetinaNet). It directly predicts the object's class and bounding box coordinates in a single pass.
Two-Stage Detector	Slower but often more accurate. It uses a Region Proposal Network (RPN) to first identify potential areas of interest and propose coarse bounding boxes for them. These proposals are then passed on for fine-tuned classification and bounding box refinement. This helps reduce false positives.

**3.2 A Deep Dive into the RetinaNet Model**

Dr. Sulagna used RetinaNet, a popular one-stage detector, as a representative example to explain the general workflow of modern object detection models.

1. Feature Extraction: A backbone network (like VGG or ResNet) processes the input image to extract a rich set of essential features (edges, textures, shapes).
2. Feature Enhancement: A Feature Pyramid Network (FPN) enhances these features at multiple scales, allowing the model to detect both large and small objects effectively.
3. Candidate Proposal & Selection: The model uses a dense grid of pre-defined anchor boxes to propose thousands of potential object locations across the image.
4. Classification & Regression: Two parallel sub-networks process the proposals. One classifies the object within each box (e.g., "stroke"), while the other refines the box's coordinates for a precise fit.

**3.3 The Crucial Step: Data Preparation and Labeling**

For a detection model to learn, it must be trained on meticulously labeled data. This step is one of the most critical and time-consuming parts of the entire process.

The speaker demonstrated the labeling workflow using the labelImg software. This tool allows a human annotator to manually draw bounding boxes around each object of interest in an image. The output of this process is an XML file for each image. This file contains the class name (e.g., "infarct") and the precise pixel coordinates (xmin, ymin, xmax, ymax) of every bounding box drawn. This structured data is what the machine uses to learn the visual features associated with an object's location and appearance.

**3.4 Key Concept: Anchor Boxes and Intersection over Union (IOU)**

To efficiently find objects, detection models use the concept of anchor boxes. These are a large set of pre-defined, template bounding boxes of various sizes and aspect ratios that are overlaid across the entire image.

The model then uses a metric called Intersection over Union (IOU) to determine which anchors are good candidates. IOU measures the percentage of overlap between a proposed anchor box and the manually labeled ground-truth box. Specifically, it is calculated as the area of overlap between the two boxes divided by the total area covered by both boxes combined (the union).

* An anchor with a high IOU (e.g., > 0.5) is considered a "positive" match, meaning it likely contains the object.
* An anchor with a very low IOU (e.g., < 0.4) is a "negative" match and is discarded as background.
* Anchors with intermediate IOU are typically ignored.

This process effectively filters thousands of initial proposals down to a few high-quality candidates. This refined set is then passed to the final classification and regression layers, which make the final prediction of the object's class and its precise bounding box.

---

## 4.0 Broader Applications of AI-driven Detection

The powerful detection techniques discussed are highly versatile and not limited to stroke analysis. Dr. Sulagna highlighted this adaptability by sharing two additional projects that apply the same core principles to different domains, demonstrating the broad utility of the technology.

**4.1 Focal Liver Lesion Detection**

This project focused on detecting very small tumors (focal lesions) in the liver from complex MRI scans. The primary challenges included the tiny size of the lesions and the complexity of integrating information from multiple MRI sequences.

The team developed an innovative workflow to address this:

1. First, they integrated features from both contrast and non-contrast MRI sequences.
2. Next, an AI model was used to detect and crop the entire liver. This step was crucial for minimizing false positives that could arise from nearby organs like the spleen or kidneys.
3. Finally, a feature voting strategy was employed to accurately identify the final lesion locations from the pooled feature data.

**4.2 Mixed Food Image Analysis**

This project aimed to automatically identify and classify food items on a plate in an elderly care facility. The goal was to monitor the nutritional intake of residents to ensure their dietary needs were being met.

The model, based on a modified EfficientNet architecture, had to handle significant complexity, including:

* Identifying single-item dishes.
* Recognizing mixed-ingredient foods (e.g., a dish containing both cabbage and carrots).
* Detecting multiple distinct dishes on a single plate.
  
---

## 5.0 Practical Implementation and Key Takeaways

The final section of the session covered a practical code demonstration and synthesized key concepts clarified during the audience Q&A session.

**5.1 Code Demonstration Highlights**

The live code demo illustrated the key steps involved in training an object detection model.

* The demonstration used a publicly available Kaggle codebase originally designed for face mask detection but was adapted to run on the speaker's own brain scan data.
* The main stages of the workflow included:
  1. Loading the training and testing images along with their corresponding XML annotation files.
  2. Importing a pre-built RetinaNet model from the torchvision library.
  3. Setting up the training parameters, such as the optimizer, learning rate, and number of epochs.
  4. Executing the training loop.
* After running for only two epochs, the preliminary result showed many noisy, overlapping bounding boxes. This effectively illustrated a key point: detection models require significant training time—often 8 to 9 hours on a powerful GPU—to converge and produce accurate, refined results.

**5.2 Insights from the Q&A Session**

The question-and-answer period provided further clarity on several practical aspects of AI implementation:

* Live Implementation: AI models are typically developed and trained offline first. Once validated, they are integrated into a hospital's clinical workflow to run in parallel with the imaging machine (e.g., CT or MRI scanner), providing real-time analysis as images are acquired.
* Medical Image Labeling: Unlike non-medical datasets where automated labeling tools may be used, medical images require secure and manual labeling by researchers or clinicians. This is due to data privacy regulations and the nuanced expertise needed to identify pathologies correctly. This manual process can take months to complete for a large dataset.
* The Role of CNNs: There is a direct relationship between labeling and the Convolutional Neural Network (CNN). The manual labels (bounding boxes) explicitly tell the CNN what features to look for and learn within an image. The CNN is the engine for feature extraction, but it needs the labeled data as a guide.
* Handling Data Variability: When faced with challenges like distinguishing between very similar-looking objects (e.g., two different types of food), the single most effective strategy is to significantly increase the size and variety of the training dataset. More examples help the model learn the subtle features that differentiate the classes.
