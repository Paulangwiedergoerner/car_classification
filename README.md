# 🚗 Car Classification Type App

## Project Overview

The Car Classification Type App is a full-stack machine learning web application designed to classify the type of a car from an uploaded image. Its objective is to automate car recognition using deep learning, offering real-time predictions through a user-friendly web interface. The system includes model training, an admin login system, a modern upload page, and a dashboard for tracking predictions.

## Dataset

The dataset used for training consists of labeled car images categorized by type (e.g., SUV, Sedan, Truck, Coupe). Each category is stored in a separate directory, which enables supervised classification. All images are preprocessed to maintain consistent dimensions and pixel scale. The source can be either a custom dataset or a public one such as the [Stanford Cars Dataset](https://ai.stanford.edu/~jkrause/cars/car_dataset.html), downloaded and organized into folders per class.

## Pipeline Steps

The pipeline begins with **data preprocessing**, where all images are resized to a fixed resolution and normalized to have pixel values between 0 and 1. The class labels are encoded into integers using label encoding. In the **feature engineering** stage, each image is transformed into a NumPy array suitable for model input. Optionally, features may be extracted using pre-trained CNNs. The **model training** step involves feeding these processed images into a deep learning classifier, which is trained to predict the correct car type. After training, **evaluation** is performed using metrics like accuracy and confusion matrix to assess model performance. Finally, in the **deployment** phase, the model is integrated into a Flask-based web application that handles file uploads, model inference, user interaction, and admin dashboard visualization.

## Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/Paulangwiedergoerner/car_classification_type.git
cd car_classification_type
```

### 2. Create and activate the virtual environment

- **Windows:**
  ```bash
  python -m venv venv
  venv\Scripts\activate
  ```

- **macOS/Linux:**
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

### 3. Install all required packages

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

> 💡 This will recreate the virtual environment (`venv/`) with all required packages.

### 4. Run the application

```bash
python app.py
```

Open your browser and go to: [http://127.0.0.1:5000](http://127.0.0.1:5000)

## Usage

🔐 **Note**: The dashboard at `/manager` is protected. Users must sign up or log in through the admin form to gain access. Unauthorized users cannot view analytics or prediction history without authentication.

After starting the app, navigate to [http://127.0.0.1:5000](http://127.0.0.1:5000) to upload a car image and receive a prediction. Admins can access [http://127.0.0.1:5000/manager](http://127.0.0.1:5000/manager) to log in, review predictions, view charts, and system usage metrics. Admin credentials are stored securely in `admin.db` (SQLite), and predictions are logged with timestamps in the dashboard table.

## Notes

- ✅ The trained model file (`resnet50_car_body_type_model.h5`) is already included under `model/` — no need to download it separately.
- ✅ Background images are available under `static/` and `static/uploads/`.
- 🧹 You can reset admin or prediction data using:

```bash
python reset_db.py
```
