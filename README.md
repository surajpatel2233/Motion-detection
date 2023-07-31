# Motion-detection
The provided code is a simple motion detection program using the OpenCV library in Python. It captures video frames from the default camera (usually the webcam), processes the frames, and detects motion between consecutive frames. When motion is detected, it draws a bounding rectangle around the moving object(s) and displays the result in real-time.

Summary of the code:
1. Import required libraries: The code imports necessary modules such as `cv2` for computer vision tasks and `numpy` for numerical computations.

2. Capture video from the camera: The code creates a video capture object `cap` and opens the default camera (camera index 0) using `cv2.VideoCapture(0)`.

3. Initial frame reading: The code reads two initial frames from the video capture, `frame1` and `frame2`, using the `cap.read()` function.

4. Motion detection loop: The code enters a loop (`while cap.isOpened()`) to continuously process video frames for motion detection until the user presses the 'q' key.

5. Motion detection algorithm: The motion detection algorithm consists of the following steps:
   a. Compute the absolute difference (`diff`) between `frame1` and `frame2` to highlight the regions where motion occurs.
   b. Convert the difference image to grayscale (`gray`) to simplify processing.
   c. Apply Gaussian blurring (`blur`) to reduce noise and smoothen the image.
   d. Threshold the blurred image (`thresh`) to create a binary image with moving objects represented as white and the background as black.
   e. Dilate the binary image (`dilated`) to fill gaps and join nearby white regions.
   f. Find contours in the dilated image to identify individual moving objects.

6. Motion detection visualization: For each contour found, the code checks its area, and if it's larger than a predefined threshold (`5000` in this case), it considers it as a moving object and proceeds to visualize it:
   a. A bounding rectangle is drawn around the moving object using `cv2.rectangle`.
   b. A text "There is Movement" is displayed at the top-left corner of the frame using `cv2.putText`.
   c. The contour of the moving object is drawn using `cv2.drawContours`.

7. Display the processed frame: The resulting frame with bounding rectangles, text, and contours is displayed in a window named "feed" using `cv2.imshow`.

8. Update frame references: After processing, `frame1` is updated to hold the value of `frame2`, and `frame2` is updated with the next frame read from the video capture. This allows the code to continuously detect motion between consecutive frames.

9. Exit condition: The loop continues until the user presses the 'q' key. When the 'q' key is pressed, the loop breaks, and the video capture is released (`cap.release()`), and all OpenCV windows are closed (`cv2.destroyAllWindows()`).

The resulting effect is a real-time motion detection display, where moving objects are outlined with bounding rectangles and marked with the "There is Movement" text. This type of motion detection can be useful for various applications, such as security systems or surveillance.
