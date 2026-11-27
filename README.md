# Ex-7 : HOUGH-TRANSFORM

## Developed By
Name: Chandru M

Register No: 212224230041

## Aim
To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

## Learning Objective
* Understand each stage of image processing
* Learn how to build a complete computer vision pipeline
* Practice writing code in guided sections

## Algorithm 

1. Start the program and import the required libraries: OpenCV, NumPy and Matplotlib.

2. Read the input image using cv2.imread() and convert the colour image into a grayscale image using cv2.cvtColor().

3. Detect edges in the grayscale image using the Canny edge detection method with threshold values 50 and 150.

4. Apply Hough Transform using cv2.HoughLinesP() to detect straight lines and obtain their coordinates.

5. Draw the detected lines on the original image using cv2.line() and display the final output using Matplotlib.

## Software Used
* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

## Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('chess.jpeg')  # Replace 'image.jpg' with your image path

# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')

plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150

# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')

# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)


# Step 6: Draw detected lines on the original image

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')

```

## Output
### Original image

<img width="389" height="410" alt="download" src="https://github.com/user-attachments/assets/e26ca492-6541-4a28-91fe-18963789d373" />


### Greyscale image

<img width="389" height="410" alt="download" src="https://github.com/user-attachments/assets/a2cd20cd-0bfc-4778-af2c-1d20da55763e" />


### Canny edge detector

<img width="389" height="410" alt="download" src="https://github.com/user-attachments/assets/a072c85e-a4d7-48ca-a536-77d0538cdeb3" />


### Hough Transform

<img width="389" height="410" alt="download" src="https://github.com/user-attachments/assets/fd1f450d-dcbc-4f3a-94f2-789f1acac4ec" />


## Result
Thus, the lane detection pipeline is successfully implemented by completing the missing code sections. The system detects and highlights lane lines effectively.
