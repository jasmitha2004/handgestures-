Hand Gesture Recognition using PyTorch
A PyTorch-based hand gesture image classification project implemented in a single Google Colab notebook.
Project Overview
This project trains a custom Convolutional Neural Network (CNN) to classify hand-gesture images from an annotated image dataset.
The complete workflow is implemented in:
Hand_Gesture_PyTorch.ipynb
The notebook handles dataset extraction, annotation-based cropping, preprocessing, CNN training, evaluation, model saving, and prediction on a new image.
Workflow
Annotated Dataset ZIP
        ↓
Extract train / valid / test data
        ↓
Read annotation CSV files
        ↓
Crop images using bounding boxes
        ↓
Create class folders
        ↓
Resize images to 128 × 128
        ↓
Data Augmentation
        ↓
PyTorch CNN
        ↓
Training
        ↓
Validation / Evaluation
        ↓
Classification Report + Confusion Matrix
        ↓
Save trained model (.pth)
        ↓
Predict a new image
Technologies Used
- Python
- PyTorch
- Torchvision
- OpenCV
- Pandas
- NumPy
- Pillow
- Scikit-learn
- Matplotlib
- Google Colab
Dataset Processing
The uploaded dataset contains image files and annotation CSV files.
For each split (train, valid, and test), the notebook:
1. Reads the annotation CSV.
2. Finds the corresponding image.
3. Reads the bounding-box coordinates:
   - xmin
   - ymin
   - xmax
   - ymax
4. Crops the annotated region.
5. Saves the cropped image inside a folder named after its class ID.
The class names are automatically obtained from the resulting folder names, so the notebook does not hard-code gesture labels.
Image Preprocessing
Images are resized to:
128 × 128
Training augmentation includes:
- Random horizontal flip
- Random rotation up to 10 degrees
- Color jitter
- Tensor conversion
- ImageNet-style normalization
Evaluation images use resizing, tensor conversion, and normalization without the training augmentations.
CNN Architecture
The custom CNN contains three convolutional blocks.
Each block uses:
- Conv2D
- BatchNorm2D
- ReLU
- MaxPool2D
The feature extractor uses:
3 → 32 → 64 → 128 channels
The classifier contains:
Flatten
    ↓
Linear(128 × 16 × 16 → 256)
    ↓
ReLU
    ↓
Dropout(0.5)
    ↓
Output layer
The number of output classes is determined automatically from the dataset.
Training
Training configuration used in the notebook:
Parameter	Value
Image size	128 × 128
Batch size	32
Epochs	10
Learning rate	0.001
Optimizer	Adam
Loss function	CrossEntropyLoss
Device	CUDA GPU if available, otherwise CPU


During training, the notebook records:
- Training loss
- Training accuracy
- Evaluation accuracy
The model with the best evaluation accuracy is saved.
Evaluation
The notebook generates:
- Classification report
- Confusion matrix
- Training loss graph
- Training accuracy graph
- Evaluation accuracy graph
The evaluation split uses the provided valid folder when available; otherwise, it uses the test folder.
Prediction
After training, the notebook allows a new image to be uploaded.
The image is:
1. Converted to RGB.
2. Resized to 128 × 128.
3. Normalized.
4. Passed through the trained CNN.
5. Converted to class probabilities using Softmax.
The notebook displays:
Predicted class: <class>
Confidence: <percentage>%
Model File
The trained model is saved as:
gesture_model.pth
The saved checkpoint contains:
- CNN model weights
- Class names
How to Run
Google Colab
1. Open Hand_Gesture_PyTorch.ipynb in Google Colab.
2. Enable a GPU if available:
   Runtime → Change runtime type → T4 GPU
3. Run the cells from top to bottom.
4. Upload the dataset ZIP when requested.
5. Wait for dataset processing and model training.
6. Review the accuracy/loss graphs.
7. Review the classification report and confusion matrix.
8. Upload a test image in the prediction cell.
9. Download gesture_model.pth if required.
Project Output
The project produces:
gesture_crops/
    train/
    valid/
    test/

gesture_model.pth
The notebook also displays example cropped images, training graphs, evaluation metrics, and prediction results.
Important Note
This implementation is an image-based gesture classification project. It does not include real-time webcam inference.
The model predicts the class represented by the dataset's annotation/class ID. Human-readable gesture names should only be assigned when the original dataset documentation provides the mapping between class IDs and gesture names.
Repository Structure
handgestures-/
│
├── Hand_Gesture_PyTorch.ipynb
└── README.md
Project Status
- Dataset processing: Complete
- Bounding-box cropping: Complete
- CNN model: Complete
- Training: Complete
- Evaluation: Complete
- New-image prediction: Complete
- Model export: Complete
- Real-time webcam: Not included
