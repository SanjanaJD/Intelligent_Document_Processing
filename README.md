# 📄 Intelligent Document Processing

## 🧠 Introduction
**Intelligent Document Processing (IDP)** is a computer vision–based system that automates document classification and text extraction using deep learning and OCR techniques.  
The model leverages **VGG-16**, a convolutional neural network (CNN), to classify images of documents into four major categories — **Receipts, Technical Papers, Newspapers, and Book Covers**.  

After classification, an **Optical Character Recognition (OCR)** stage powered by **PaddleOCR** extracts relevant information such as transaction totals, publication titles, or author names.  
This combination of CNN and OCR provides both **document understanding** and **data extraction**, enabling efficient, accurate, and domain-specific document processing for enterprises and researchers.

---

## 🎯 Problem Definition
Traditional document processing pipelines rely heavily on generic OCR systems, which:
- Lack contextual understanding of different document types  
- Struggle with complex layouts or skewed images  
- Fail to extract structured data efficiently  

This project addresses these challenges by building a hybrid pipeline that:
1. Detects and corrects document orientation using **YOLOv8 + Hough Transform**.  
2. Classifies document types using **VGG-16 CNN**.  
3. Extracts text with **PaddleOCR**, applying category-specific parsing rules.  

The result is a smarter, faster, and more interpretable document processing solution.

---

## 📚 Literature Survey
This work builds upon prior research in computer vision and OCR:

- **M. Kumar & R. Bhatt (2022)** — Real-time object detection using YOLO and OpenCV for accurate bounding boxes.  
- **R. Mittal & A. Garg (2020)** — Comprehensive OCR review highlighting modern extraction engines like Tesseract and PaddleOCR.  
- **Mahardi et al. (2020)** — Fine-tuned VGG models for image classification, achieving >98% accuracy on image datasets.  
- **Y.J. Ma et al. (2021)** — PaddlePaddle’s architecture and applications in large-scale OCR tasks.  
- **P. Ganesan & G. Sajiv (2017)** — Comparative study of edge detection methods for robust preprocessing.

---

## ⚙️ Technical Approach

### A. 🧩 Image Processing and Object Detection
1. **Edge Detection** – Fine-tuned **YOLOv8** detects document boundaries for precise cropping.  
2. **Geometric Transformations** – The system applies **Hough Transform** and **Perspective Warping** to correct skew and standardize document orientation.  
3. **De-skewing** – Affine transformations ensure alignment and readability for downstream OCR.

### B. 🧠 Image Classification
- Utilizes **VGG-16**, a 16-layer CNN known for its simplicity and accuracy in feature extraction.  
- Classifies documents into one of four categories:
  - Receipts  
  - Technical Papers  
  - Newspapers  
  - Book Covers  

**Training Accuracy:** 88.18%  
**Validation Accuracy:** 75.10%  

### C. 🔍 Optical Character Recognition (OCR)
After classification, **PaddleOCR** performs high-accuracy text detection and recognition.  
Extracted bounding boxes and coordinates are processed using **regex patterns** customized per document type:

| Document Type | Extracted Information |
|----------------|----------------------|
| **Receipts** | Date, itemized prices, total expenses |
| **Technical Papers** | Title, author(s), conference title |
| **Newspapers** | Newspaper name, publication date |
| **Book Covers** | Book title, author name |

This structured extraction ensures context-aware accuracy and data consistency.

---

## 🧪 Results

### ✅ Classification
- **Training Accuracy:** 88.18%  
- **Validation Accuracy:** 75.10%  
- VGG-16 effectively differentiated between document categories.

### 🧾 OCR Outputs
- **Receipts:** Detected and extracted *date* and *total amount* using bounding boxes with high confidence.  
- **Book Covers:** Successfully recognized *title* and *author name*.  
- **Newspapers:** Identified *publication title* (“THE WALL STREET JOURNAL”) with strong confidence.  

### 🖼️ Sample Results
| Stage | Description |
|--------|--------------|
| Edge Detection | Detected contours using YOLOv8 and Hough Transform |
| Warping | Corrected perspective and standardized the document view |
| OCR Output | Extracted text regions with confidence scores and bounding boxes |

---

## 📈 Evaluation Metrics

| Component | Technique | Accuracy / Confidence |
|------------|------------|----------------------|
| Document Classification | VGG-16 CNN | 75% validation accuracy |
| OCR Detection | PaddleOCR | Avg. confidence > 90% |
| Skew Correction | Hough Transform + Warp | Manual inspection verified consistency |

---

## 🧰 Tools and Frameworks

| Category | Technology |
|-----------|-------------|
| Deep Learning | TensorFlow / Keras (VGG-16) |
| Object Detection | YOLOv8 |
| OCR Engine | PaddleOCR |
| Image Processing | OpenCV |
| Data Handling | NumPy, Pandas |
| Visualization | Matplotlib, Seaborn |
| Development | Jupyter Notebook, VSCode |

---

## 🧩 System Architecture

    +--------------------------+
    |  Input Document Image    |
    +--------------------------+
                 ↓
       YOLOv8 Edge Detection
                 ↓
       Hough Transform & Warping
                 ↓
        VGG-16 Classification
                 ↓
          PaddleOCR Extraction
                 ↓
    Regex Parsing & Information
                 ↓
       Final Structured Output



---

## 🚀 Future Work
- 🔁 **Hybrid CNN + Attention Models:** Integrate attention mechanisms to enhance classification precision.  
- 📷 **Robust Preprocessing:** Extend support for side-angled or low-light document images.  
- 🧠 **Multilingual OCR:** Enable extraction from diverse language scripts.  
- ☁️ **Deployment:** Containerize using Docker and integrate APIs for enterprise document workflows.  

---

## 💬 Conclusion
The **Intelligent Document Processing System** achieved:
- 88% training accuracy and 75% validation accuracy in classification  
- High-confidence OCR extraction for multiple document formats  

By combining **VGG-16**, **YOLOv8**, and **PaddleOCR**, the system demonstrates strong potential for real-world deployment in document automation workflows.  
Future improvements such as attention-based models and enhanced preprocessing will make the system even more robust and versatile.


---


