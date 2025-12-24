## Session: Introduction to Image Preprocessing Methods

**Speaker:** Dr. Sulagna Mohapatra  
**Designation:** AI & Automation Strategic Architect  
**Organization:** Volktek Corporation, Taiwan  
**Topic:** Introduction to Image Preprocessing Methods  

> These notes reflect my understanding of the session delivered during the Winter School on Biomedical Image Processing and Its Applications.
Understood.
> 
## Introduction: Preparing Medical Images for Artificial Intelligence

Before an artificial intelligence (AI) model can analyze a medical image like a CT scan or MRI, the image must be carefully prepared. This crucial set of steps, known as **pre-processing**, serves to clean, enhance, and focus the image data, transforming a raw scan into a format that a machine can effectively analyze. Without this foundational work, even the most advanced AI models can produce inaccurate and unreliable results.

From a machine's perspective, a picture is not a visual scene but a grid of numbers called pixels. The value of each pixel determines its appearance. Understanding the fundamental types of images is the first step in learning how to prepare them for analysis.

* **Binary Image:** This is the simplest type, where each pixel has only one of two values, typically 0 for black and 1 for white.
* **Grayscale Image:** This type contains various shades of gray. Each pixel has a value that typically ranges from 0 (pure black) to 255 (pure white), allowing for 256 distinct shades.
* **RGB (Color) Image:** Composed of three separate color channels—Red, Green, and Blue—this format can represent a vast spectrum of colors, with 2 to the power of 24 (16,777,216) possible values. It is important to note that many medical images that appear gray to the human eye are technically stored as RGB images, a detail that becomes critical during pre-processing.

But why is this meticulous preparation process so indispensable for building effective medical AI? The following section explores the critical motivations behind image pre-processing.

---

## 1. The "Why": The Critical Need for Pre-processing

Feeding raw image data directly to an AI model is an inefficient and often ineffective strategy. It can lead to poor performance, slow training times, and ultimately, inaccurate results. The strategic goal of pre-processing is to refine the input data, focusing the model's attention on the most relevant information while removing irrelevant "noise" that could otherwise confuse it. This step is not merely technical; it is a critical part of building an intelligent and reliable system.

Here are the key motivations for pre-processing medical images:

1. **Removing Unwanted Information**
   Raw medical images frequently contain large areas that are irrelevant to the diagnostic task. For example, a CT scan of a brain is often surrounded by a significant black background. This is based on **her own Ph.D. work analyzing non-contrast CT data for ischemic stroke; if this raw image is fed to a model, the model may be negatively affected by this large, meaningless area**. Pre-processing techniques like cropping can eliminate this unwanted information, allowing the model to concentrate solely on the cerebral part of the image.

2. **Focusing on the Subject**
   An AI model can sometimes learn the wrong patterns if the data is not properly focused. In a project designed for elderly care, an AI model intended to analyze the food on a dinner plate was found to be focusing more on the plate itself than the food. This illustrates a common pitfall: without guidance, a model may latch onto irrelevant features. Pre-processing helps isolate the true subject of interest, ensuring the AI learns from the right signals.

3. **Reducing Confusion for the Model**
   Medical images can be complex, containing numerous features that might distract an AI from its primary target. In an analysis of intracranial stenosis (narrowing of an artery in the brain), the target artery is surrounded by many other arteries. This visual clutter can easily confuse a model tasked with detecting an occlusion. Through pre-processing, it's possible to isolate the specific artery with the suspected issue, dramatically simplifying the task and improving the model's ability to make an accurate detection.

Having established why pre-processing is so vital, we can now explore the specific methods used to accomplish these goals.

---

## 2. The Four Pillars of Medical Image Pre-processing

While there are countless techniques available, the majority of pre-processing tasks in medical imaging can be organized into four main categories. The choice of which method to use is not arbitrary; it depends entirely on the specific data and the problem you are trying to solve. These pillars represent the core operations used to transform raw data into high-quality input for AI models.

The four pillars are:

* Noise Removal and Image Enhancement
* Region of Interest (ROI) Extraction
* Cropping
* Morphological Operations

The following subsections will explore each of these pillars in detail, explaining their purpose and common methodologies.

---

## 2.1. Pillar 1: Noise Removal and Image Enhancement

"Noise" refers to random variations in brightness or color in an image that can obscure important details. It can arise from various sources, such as faulty scanner equipment or the inherent limitations of an imaging technique. Non-contrast CT scans, for example, are often less clear than their contrast-enhanced counterparts. **In her experience analyzing data for brain stroke and kidney stone detection, applying these filtering methods was a critical step for enhancing the images.** The purpose of noise removal is to reduce these variations and enhance the overall quality of the image, making critical features more visible.

To remove noise effectively, you should follow a structured sequence of steps:

1. **Read the Image:** The process begins by loading the digital image file into the system.
2. **Convert to Grayscale:** Although an image may look gray, it is often stored in a three-channel RGB format. Converting it to a single-channel grayscale image is a common first step. This simplifies computation significantly by reducing the number of possible pixel values from 2 to the power of 24 down to just 256, without losing essential information for many medical tasks.
3. **Add Known Noise:** This counter-intuitive step is crucial for quantification. Imagine being given a glass of Coke and a glass of black tea and asked to tell them apart at a glance. It's difficult. However, if you add a Mentos to the glass of Coke, the immediate fizzy reaction instantly identifies it. The known noise is our "Mentos." By adding a known type and amount of noise (e.g., Gaussian noise), we establish a clear "comparison parameter." This allows us to use a metric like PSNR to precisely measure the total noise in the image, giving us a quantitative target for our filtering methods to meet.
4. **Quantify Noise with PSNR:** With a known amount of noise added, we can now quantify the total noise level using a metric called **Peak Signal-to-Noise Ratio (PSNR)**. PSNR measures image quality, and a higher PSNR value generally indicates a clearer, less noisy image.
5. **Apply a Filtering Method:** Filters are algorithms designed to remove noise. There are many types, each suited for different kinds of noise. In an analysis of a brain image, a `median filter` was found to produce the highest PSNR value, indicating it was the most effective method for that specific case.

By applying this process, a noisy, non-contrast CT image can be transformed into an enhanced, clearer version. In the case of a stroke analysis, this enhancement made the affected region more visible, providing a much better input for the subsequent AI model. After cleaning the image, the next logical step is to isolate the most important parts of it.

---

## 2.2. Pillar 2: Region of Interest (ROI) Extraction

Region of Interest (ROI) extraction, also known as **segmentation**, is the process of separating the foreground from the background. The "foreground" is the object of primary interest—such as a tumor, a specific organ, or a group of cells—while the "background" is everything else. The goal is to create a mask or outline that precisely identifies the ROI, allowing the AI model to ignore all irrelevant surrounding tissue and structures. The choice between these methods depends entirely on the characteristics of the image; a high-contrast hemorrhage might only need simple thresholding, while a complex tumor with varying intensities demands a more adaptive approach.

### 2.2.1. Thresholding-Based Methods

So, how does thresholding work? At its core, it's about setting a cutoff point to separate objects from the background based on pixel intensity. Pixels above or below this "threshold" are classified as either foreground or background.

* **Global Thresholding:** This method applies a *single* threshold value across the entire image. It is most effective when there is a clear and high contrast between the object of interest and its surroundings, such as a bright hemorrhage against darker brain tissue.
* **Local (Adaptive) Thresholding:** This more advanced method is used when an image has varying lighting conditions or intensity levels in different areas. For example, a brain tumor might have an older, darker region and a newer, brighter region. Instead of one global threshold, this technique slides a small "window" across the image, calculating a unique threshold for each local neighborhood of pixels based on its specific brightness and contrast.

Another related technique is **Intensity-Level Slicing**, which highlights a specific *range* of pixel intensities. This is particularly useful when an organ or tissue type has a known and consistent intensity signature, such as the lungs in a CT scan.

---

## 2.2.2. Clustering-Based Methods

Clustering is an unsupervised machine learning method where an algorithm automatically groups pixels with similar characteristics (like color or intensity) into distinct "clusters." The user does not need to define a threshold; instead, the algorithm finds natural groupings in the data.

A popular example is **K-Means clustering**. In this method, the user specifies the desired number of clusters (`K`). The algorithm then iteratively assigns each pixel to the nearest cluster center and recalculates the centers until the clusters are stable. In one brain scan analysis, setting K=3 successfully isolated the ROI into its own distinct, green-colored cluster, separating it from the background and other brain tissue.

---

## 2.2.3. Contouring-Based Methods

Contouring methods focus on the **shape** and **continuity** of regions. Instead of looking at individual pixel values, these algorithms work by joining all the points along a boundary that share a similar intensity, effectively tracing the outline of an object.

The **Superpixel** method is a modern contouring-based approach. It groups pixels into small, perceptually meaningful regions called superpixels. The output divides the image into multiple colored segments based on shape continuity, with the number of segments controllable by the user. This is useful for breaking down a complex image into simpler, shape-based components.

---

## 2.2.4. Edge-Based Methods

Where contouring-based methods build regions by following paths of *similarity*, edge-based methods achieve the opposite: they define an object by finding the *abrupt changes* at its boundaries. They identify the edges of objects by detecting discontinuities, or sharp transitions in brightness, which almost always correspond to the boundary between one object and another.

Popular edge detection algorithms include **Canny, Robert, Sobel, and Prewitt**. The Canny method, in particular, often provides the clearest and most accurate results for medical images. For instance, in an image of a spreading brain tumor, these methods can effectively outline the boundary of the tumor, providing crucial information about its shape and extent. In another clinical case involving a liver cyst, the doctor needed to know if two cysts were touching, as physical contact significantly increases the risk of the cysts brushing and causing complications. Precise edge detection is the only way to answer such a critical diagnostic question.

---

## 2.3. Pillar 3: Cropping

Cropping is a simple yet highly effective pre-processing technique for removing large, unnecessary portions of an image. Its primary purpose is to narrow the field of view to only the relevant area. For example, by cropping out the large black background surrounding a brain scan, we ensure that the AI model's computations are focused exclusively on the brain tissue itself.

This can be accomplished using two main algorithmic approaches:

* **Derived Algorithm:** The image is cropped automatically by programmatically identifying the boundaries of all non-zero pixels and creating a bounding box around them.
* **Static Values:** A user manually defines the pixel coordinates for the top, bottom, left, and right boundaries of the crop box.

From this simple geometric operation, we now move to more complex manipulations based on an object's shape.

---

## 2.4. Pillar 4: Morphological Operations

Morphological operations are a set of techniques that process an image based on its **shape**, or morphology. These methods use a small, predefined shape called a **structuring element** (e.g., a disk, square, or diamond) that slides over the image like a filter. As it moves, it modifies pixels based on how the structuring element interacts with the shapes in the image, allowing for powerful shape-based manipulations.

* **Erosion:** This operation removes small, isolated noise pixels (islands) and can shrink the boundaries of the primary object. It is useful for cleaning up a binary image after thresholding.
* **Dilation:** The opposite of erosion, dilation expands the boundaries of objects. It is useful for filling small holes or connecting narrow gaps within an object.
* **Opening:** This is simply an erosion followed by a dilation. Its primary use is to remove small protrusions and smooth the contour of an object without significantly changing its overall size.
* **Closing:** This is a dilation followed by an erosion. It is effective for fusing narrow breaks and filling small holes within an object, making it more solid.
* **Top-Hat Transformation:** This operation returns objects that are smaller than the structuring element and brighter than their surroundings, making it ideal for isolating small, bright features.
* **Black-Hat Transformation:** The inverse of the Top-Hat, this returns objects that are smaller than the structuring element and darker than their surroundings.
* **Morphological Gradient:** This is calculated as the difference between an image's dilation and its erosion. Its main purpose is to find the precise boundary or outline of an object.

In short, use **Opening** to clean up small, unwanted objects and smooth outer contours, and use **Closing** to repair gaps and holes *within* your main object of interest. These individual techniques are powerful on their own, but their true utility is revealed when they are combined in a sequence to solve a complex problem.

---

## 3. Putting It All Together: A Liver Cyst Segmentation Example

In practice, a single pre-processing task rarely relies on just one operation. More often, it requires a carefully designed sequence of different techniques, each step building on the last. This section walks through a real-world example of isolating a liver cyst from a non-contrast CT image to demonstrate how these methods are combined into a cohesive workflow.

The process began by addressing the image's low quality, a common issue with non-contrast scans. The goal was to segment the liver cyst with high precision, removing all surrounding tissue.

1. **Image Enhancement:** To tackle the low contrast, a `guided filter` was first applied to the image. This enhanced the boundaries of the cyst, making it more distinct from the surrounding liver tissue.
2. **Binarization:** Next, `global thresholding` was used to convert the enhanced grayscale image into a binary (black and white) image. This crucial step made the cyst stand out as a clear white region against a black background.
3. **Initial Cleanup:** The binarized image wasn't perfect; it contained small, noisy white spots that were not part of the cyst. To eliminate these, a `BW area open` operation with a threshold of 800 was applied. This effectively removed any group of white pixels smaller than the threshold, cleaning up the background.
4. **Refining the ROI:** Now focusing on the cyst itself, a `closing` operation was used to smooth its boundary and fill in any small holes or gaps within it. Using the `neighborhood` as the structuring element, this step resulted in a solid, clean representation of the ROI.
5. **Final Extraction:** Finally, the clean binary image from the previous step was used as a mask on the original, enhanced image. This extracted the cyst perfectly, removing the entire surrounding background.

This multi-step process shows how a sequence of filtering, thresholding, and morphological operations can successfully isolate a complex ROI, providing a clean and focused input ready for an AI model. However, even with these powerful tools, there are important limitations to consider.

---

## 4. Key Considerations and the Limits of Pre-processing

Now, you might be thinking that these techniques can solve any problem. But as with any tool, it's crucial to understand their limitations. While pre-processing is a fundamental and indispensable part of the medical AI pipeline, it is not a silver bullet. Certain challenges require more advanced solutions that go beyond these traditional techniques.

* **The Challenge of Overlapping Intensities:** Sometimes, a diseased area and the surrounding healthy tissue have very similar pixel intensity values, making separation with simple thresholding or segmentation impossible. This is precisely where advanced AI segmentation models, which learn to distinguish tissues based on texture, shape, and context from thousands of labeled examples, become necessary.
* **The Problem of Scanner and Institutional Bias:** An AI model trained exclusively on images from one hospital's scanner may perform poorly on images from a different scanner at another institution. This is due to subtle differences in image parameters. The solution is to conduct **multi-institutional studies**, training models on diverse data from multiple sources to make them more robust and generalizable.
* **The Importance of Longitudinal Data:** Analyzing a single "time instance" scan can be informative, but it doesn't capture the full picture of a disease. A **longitudinal study**, which analyzes a patient's scans over time, can reveal crucial patterns of disease progression or regression that might be completely missed in a single image.
* **The Move to Multimodal Analysis:** Images alone do not always tell the full story. A truly comprehensive diagnosis often requires more context. This has led to the rise of **multimodal data** analysis, where AI models combine image data with other sources of information—such as clinical reports, patient demographics, and lab results—to produce far more accurate and reliable predictions.

Ultimately, image pre-processing is the essential first step in the sophisticated pipeline of modern medical AI. It is the art and science of preparing the canvas upon which complex models can perform their powerful analysis.

---
