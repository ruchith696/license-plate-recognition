# License Plate Recognition
The idea is to recognise license plate number of a car. 

## Method
1. Detect License Plate
2. Perform segmentation of characters
3. Train a ML model to predict characters
4. Prediction of characters in License Plate


The approach used to segment the images is Connected Component Analysis. Connected regions wil imply that all the connected pixels belong to the same object. A pixel is said to be connected to another if they both have the same value and are adjacent to each other.

Car Image -> Grayscale Image -> Binary Image -> Applying CCA to get connected regions -> Detect license plate out of all connected regions (Assumptions made : width of the license plate region to the full image ranges between 15% and 40% and height of the license plate region to the full image is between 8% & 20%)

Output of first step is a license plate image detected in a car image. This is provided as input to step2 and CCA is applied on this image to bound the characters in plate.Each character identified is appended into a list.

Model is trained using SVC (4 cross fold validation) and neural network with dataset present in directory train20X20. The models are saved as finalized_model.sav and model.h5 which is then loaded to predict each character.

Once the characters of plate is obtained and model is trained, the model is loaded in order to predict each character.

## Setup

Clone the repository. Change the path of the image/video file in DetectPlate.py Run PredictCharacters.py. This will load the trained model (finalized_model.sav / model.h5) which is added to repo for reference. Your own model can also be trained using the dataset attached in repo. Running PredictCharacters.py first gives grayscale and binary image. Then produces gray image with license plate bounded inside a rectangle. Each characters are also segmented and shown within boxes. Finally the model predicts the license plate.
