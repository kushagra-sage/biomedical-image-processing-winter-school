# Key Takeaways – Traditional vs. Customized CNN for Image Analysis

- Medical image analysis problems must first be translated into **well-defined computer vision tasks**, such as classification, localization, detection, or segmentation, to ensure correct model design.

- **Classification** is the foundational task in computer vision, forming the basis for more advanced tasks like detection and segmentation.

- **Classification + localization** extends basic classification by identifying the approximate location of a single object using a bounding box.

- **Detection** enables identification of multiple objects within a single image, each with its own bounding box and class label.

- **Segmentation** provides the most detailed spatial information by outlining objects at the pixel level, making it essential for precise measurement and clinical assessment.

- All CNN-based image analysis models share a **universal two-part architecture** consisting of a feature extractor and a classifier (prediction head).

- The **feature extractor** learns hierarchical visual patterns such as edges, textures, and shapes through convolutional and pooling layers.

- The **classifier head** converts extracted features into final predictions using fully connected layers.

- CNN architectures can be categorized structurally into **sequential models** (e.g., VGG16, AlexNet) and **functional models** (e.g., ResNet, Inception), with functional models allowing more complex connections.

- From an implementation perspective, CNNs can be **default (pre-trained/state-of-the-art)** or **customized**, depending on task requirements.

- **Partial customization** involves modifying existing architectures, while **full customization** requires designing a network from scratch inspired by known principles.

- Image classification problems can be **binary, multi-class, or multi-label**, each requiring different output configurations.

- Input data strategies such as **ROI cropping, patch-based processing, and data augmentation** play a critical role in improving model performance and generalization.

- **Data augmentation** helps increase dataset size, introduce variability, and reduce overfitting, especially in medical imaging where data is limited.

- Core CNN layers—including convolution, activation, pooling, flattening, dense layers, and dropout—each serve a distinct and essential role in learning and generalization.

- Proper dataset splitting into **training, validation, and testing sets** is crucial for reliable performance evaluation.

- The session emphasized that understanding CNN fundamentals is essential before advancing to **hyperparameter tuning and hands-on model implementation**.

