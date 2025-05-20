# 3D Scene Reconstruction Using SIFT and ORB

## Project Overview
This project aims to perform **3D scene reconstruction** using images captured from different perspectives.  
The main objective is to compare the effectiveness of two feature detectors: **SIFT** (Scale-Invariant Feature Transform) and **ORB** (Oriented FAST and Rotated BRIEF).  
The comparison focuses on **keypoint count**, **matching accuracy**, and **reconstruction quality**.  

---

## Methodology

### 1. Image Capture
- Captured two high-resolution images of a **laptop** from slightly different perspectives.  
- Ensured at least **60% overlap** to capture sufficient parallax.  
- Maintained consistent lighting and minimized camera shake for clear, sharp images.  
- Chose a scene with distinct edges and patterns around the **keyboard and screen area**.  

---

### 2. Feature Detection and Matching

#### SIFT (Scale-Invariant Feature Transform)
- Known for high accuracy in detecting and matching keypoints.  
- Used **OpenCV** for feature extraction and matching.  
- Applied **BFMatcher** with cross-checking to ensure robustness.  
- Keypoints Detected:  
  - **Image 1:** 24,161  
  - **Image 2:** 22,821  
- Matching Accuracy: **16.77%**  

#### ORB (Oriented FAST and Rotated BRIEF)
- Efficient and faster, but less accurate compared to SIFT.  
- Keypoints Detected:  
  - **Image 1:** 500  
  - **Image 2:** 500  
- Matching Accuracy: **8.05%**  

---

### 3. Triangulation and 3D Reconstruction
- Estimated the **fundamental matrix** using the **8-point algorithm** and **RANSAC** to filter outliers.  
- Derived the **essential matrix** to compute the camera pose.  
- Performed **triangulation** to estimate the **3D coordinates** of matched points.  
- Visualized the **point cloud** using Matplotlib.  
- **SIFT-based reconstruction** resulted in a **denser and more accurate point cloud** compared to ORB.  

---

## Challenges and Solutions

### Insufficient Keypoints with ORB
- Problem: ORB detected significantly fewer keypoints than SIFT, leading to sparse matching.  
- Solution: Optimized ORB parameters and increased iterations for better feature detection.  

### Lighting Variability
- Problem: Inconsistent lighting caused variations in keypoint detection.  
- Solution: Used **diffuse lighting** and adjusted exposure for uniform image quality.  

### Perspective Issues
- Problem: Nearly identical image angles led to poor parallax.  
- Solution: Increased angle difference between image capture positions for improved depth perception.  

---

## Results and Comparison

### SIFT vs. ORB
- **SIFT:** Superior in keypoint detection and matching accuracy, resulting in dense 3D reconstruction.  
- **ORB:** Faster but less accurate, with sparse and less structured 3D point clouds.  

| Feature       | SIFT        | ORB        |
|--------------|------------|------------|
| Keypoints     | 24,161 / 22,821 | 500 / 500 |
| Matching Accuracy | 16.77% | 8.05% |
| Reconstruction | Dense, Accurate | Sparse, Incomplete |

### 3D Point Cloud Visualization
- **SIFT:** Revealed laptop structure with high precision.  
- **ORB:** Sparse reconstruction, highlighting a trade-off between speed and accuracy.  

---

## Conclusion
The project successfully demonstrated **3D scene reconstruction** using both SIFT and ORB.  
- **SIFT** is more suitable for applications requiring **accuracy and detail**.  
- **ORB** is faster but may be acceptable for applications prioritizing **speed**.  
- Future improvements include integrating **hybrid methods** to balance accuracy and computational efficiency. 
