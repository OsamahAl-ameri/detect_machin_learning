## PROJECT TEAM

- Ammmar Abdulkareem Mohammed Daer (202174057)
- Osamah Abdulbaqi Esmael Abdullah (202174216)

## Overview

This Python project uses the YOLO (You Only Look Once) object detection model from the Ultralytics library to classify hand gestures in a video stream (Paper, Rock, Scissors). The code captures video from an external webcam, processes each frame using a pre-trained YOLO model, and displays the detected class (gesture) with a bounding box and confidence score. The project integrates the `cv2` and `cvzone` libraries for image handling and display.

## Code Explanation

1. **Imports**:
    - `ultralytics.YOLO`: Import the YOLO model to perform object detection.
    - `cvzone`: A utility library for computer vision, used here to display text on images.
    - `cv2`: OpenCV, a powerful library for handling image and video operations.
    - `math`: To perform mathematical operations like rounding the confidence score.

2. **Video Capture**:
    ```python
    cap = cv2.VideoCapture(1)
    ```
    Captures video feed from an external webcam (specified by the ID 1). Change the index to 0 if you want to use your internal webcam.

3. **Model Initialization**:
    ```python
    model = YOLO('best.pt')
    ```
    Loads the pre-trained YOLO model, specified by `'best.pt'`. This model is trained to recognize specific classes (e.g., Paper, Rock, Scissors).

4. **Class Names**:
    ```python
    classnames = ['Paper', 'Rock', 'Scissors']
    ```
    Defines the possible gesture classes that the model will recognize.

5. **Main Loop**:
    - Continuously reads frames from the webcam using `cap.read()`. If no frame is returned, the loop breaks.
    - Each frame is resized to 640x480 pixels to standardize the input size for the model.
    - The YOLO model processes the frame using `stream=True`, which returns the bounding boxes, class labels, and confidence scores for detected objects.

6. **Bounding Box & Classification**:
    - For each detected object, the bounding box coordinates `(x1, y1, x2, y2)`, confidence score, and class label are retrieved.
    - If the confidence score is greater than 50% and the detected class index is valid, a bounding box is drawn around the detected object using `cv2.rectangle`.
    - The class name and confidence percentage are displayed using `cvzone.putTextRect`.

7. **Display the Frame**:
    - The processed frame, with bounding boxes and labels, is displayed in a window using `cv2.imshow('frame', frame)`.
    - The loop continues until the user presses the 'q' key.

8. **Cleanup**:
    - After exiting the loop, the video capture is released with `cap.release()` and all OpenCV windows are closed using `cv2.destroyAllWindows()`.

This code is a basic demonstration of using a pre-trained YOLO model to recognize hand gestures in real-time from a webcam feed.

## Images

- **Accuracy**:  
     
![Capture](https://github.com/user-attachments/assets/ec895f06-7afb-4d2f-86c0-b51dc97a2fb7)

- **Size Distribution**:  
 ![Capture](https://github.com/user-attachments/assets/4f40718e-2071-47c6-adb4-7736cede2c54)

- **Histogram of Object Count by Image**:
![Capture](https://github.com/user-attachments/assets/8307ae4f-e6c2-4185-af5e-5b98d58761eb)


