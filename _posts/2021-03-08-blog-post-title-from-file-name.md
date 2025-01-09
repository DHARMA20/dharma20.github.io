## TIL-OpenCV basics

Today I used OpenCV for the first time to extract table from an image.
OpenCV (Open Source Computer Vision Library) is useful for computer vision tasks.

---

### Installation
To install OpenCV package in python using pip. Paste the following command in the terminal.
```python
pip install opencv-python
```

### Reading a file

```python
import cv2

#open and read a file
image = cv2.imread("....\image.jpg")
```

### Saving an image

It will save the image in the given path with as `filename.jpg`.
```python
cv2.imwrite('...\filename.jpg',image)
```

### Displaying an image

To Display an image, we use `imshow`. The `waitkey(0)` makes sure to pause the window with displayed image and waits till any key is pressed. After any key is pressed, `destroyAllWindows` cleans up all the resources allocated for displaying the image.
```python
  cv2.imshow('Image',image)
  cv2.waitKey(0)
  cv2.destroyAllWindows()
```
