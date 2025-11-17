# OCR & Barcode Scanner 

##  Project Overview

This project is an **OCR (Optical Character Recognition) and Barcode Scanning System** built in **Google Colab**, capable of:

* Detecting **text** from product images using **EasyOCR**
* Detecting **barcodes/QR codes** using **pyzbar**
* Guessing the product name from extracted text
* Searching the product in **MongoDB** and **OpenFoodFacts API**
* Displaying nutritional information (if available)

This satisfies the core requirement of the assignment: *build a working OCR + barcode detection pipeline that extracts product text and identifies the item.*

---

##  Project Structure

```
ocr_project/
│-- cli_scan.py        # CLI tool to scan image and extract OCR + barcode
│-- ocr_utils.py       # Helper functions (OCR, barcode, API lookup)
│-- sample images       # Contains example product images
│-- README.md
```

---

##  How to Run This Project in Google Colab

### **1. Upload Project Files**

Upload the `ocr_project.zip` folder and extract it.

### **2. Install Dependencies**

```python
!pip install easyocr
!pip install pymongo
!pip install python-barcode
!pip install pyzbar
!apt-get install -y libzbar0
```

### **3. Upload a Product Image**

```python
from google.colab import files
uploaded = files.upload()
```

Upload a **clear product image** (front-facing and readable text).

### **4. Run the CLI Scanner**

```python
!python3 /content/cli_scan.py /content/sample_product.jpg
```

### Expected Output:

* Extracted OCR text
* Detected barcode (if any)
* Product name guess
* MongoDB or OpenFoodFacts match (if available)

---

##  Core Features Implemented

###  OCR Text Extraction (EasyOCR)

Reads product names, labels, ingredients, etc.

###  Barcode Detection (pyzbar)

Detects **EAN-13**, **UPC**, **QR codes**, and more.

###  Product Name Guessing Algorithm

Cleans text and extracts high-confidence product names.

###  MongoDB Lookup

Tries to match the product name with your local database.

###  OpenFoodFacts API Integration

If MongoDB fails → checks global API for product data.

###  CLI Script Working End‑to‑End

User runs a single command:

```
python3 cli_scan.py <image_path>
```

And receives complete OCR + product lookup output.

---

##  Sample Image Used

A clear product image (Tropicana juice bottle) was generated to ensure the system detects:

* Distinct product text
* Readable label
* OCR-friendly fonts

---

##  Testing Instructions

1. Try multiple product images.
2. Ensure good lighting and no blur.
3. Crop the image if detection fails.

---

##  Limitations (as required in assignment)

* OCR depends on image quality
* Barcode detection may fail if image is blurry or angled
* OpenFoodFacts may not have every product
* No advanced error‑handling for unusual images

---

##  Conclusion

This project includes requirements like:

* OCR extraction
* Barcode detection
* Product name identification
* External database lookup
* Fully working CLI tool

