# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

```
# Developed By: [Your Name]
# Register No: [Your Register Number]

import cv2
import matplotlib.pyplot as plt
import numpy as np

# Step 1 & 2: Read image and convert to RGB for Matplotlib
img = cv2.imread("input.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
rows, cols, _ = img.shape

# -------------------------------------------------------------
# Step 3: Image Translation (Shift 50 px right, 80 px down)
# -------------------------------------------------------------
M_trans = np.float32([[1, 0, 50], [0, 1, 80]])
img_translated = cv2.warpAffine(img_rgb, M_trans, (cols, rows))

plt.figure(figsize=(8, 4))
plt.subplot(1, 2, 1), plt.imshow(img_rgb), plt.title("Original")
plt.axis("off")
plt.subplot(1, 2, 2), plt.imshow(img_translated), plt.title(
    "Translated (+50, +80)"
)
plt.axis("off")
plt.show()

# -------------------------------------------------------------
# Step 4: Image Scaling (0.5x Downscale, 2.0x Upscale)
# -------------------------------------------------------------
img_down = cv2.resize(img_rgb, None, fx=0.5, fy=0.5, interpolation=cv2.INTER_AREA)
img_up = cv2.resize(img_rgb, None, fx=2.0, fy=2.0, interpolation=cv2.INTER_CUBIC)

plt.figure(figsize=(10, 4))
plt.subplot(1, 3, 1), plt.imshow(img_rgb), plt.title("Original")
plt.axis("off")
plt.subplot(1, 3, 2), plt.imshow(img_down), plt.title("Downscaled (0.5x)")
plt.axis("off")
plt.subplot(1, 3, 3), plt.imshow(img_up), plt.title("Upscaled (2.0x)")
plt.axis("off")
plt.show()

# -------------------------------------------------------------
# Step 5: Image Shearing (Horizontal & Vertical)
# -------------------------------------------------------------
# Horizontal Shearing (shear factor = 0.3)
M_shear_x = np.float32([[1, 0.3, 0], [0, 1, 0]])
img_shear_x = cv2.warpAffine(
    img_rgb, M_shear_x, (int(cols + 0.3 * rows), rows)
)

# Vertical Shearing (shear factor = 0.3)
M_shear_y = np.float32([[1, 0, 0], [0.3, 1, 0]])
img_shear_y = cv2.warpAffine(
    img_rgb, M_shear_y, (cols, int(rows + 0.3 * cols))
)

plt.figure(figsize=(10, 4))
plt.subplot(1, 3, 1), plt.imshow(img_rgb), plt.title("Original")
plt.axis("off")
plt.subplot(1, 3, 2), plt.imshow(img_shear_x), plt.title("Horizontal Shear")
plt.axis("off")
plt.subplot(1, 3, 3), plt.imshow(img_shear_y), plt.title("Vertical Shear")
plt.axis("off")
plt.show()

# -------------------------------------------------------------
# Step 6: Image Reflection (Flipping)
# -------------------------------------------------------------
img_flip_h = cv2.flip(img_rgb, 1)  # 1 = Horizontal
img_flip_v = cv2.flip(img_rgb, 0)  # 0 = Vertical
img_flip_hv = cv2.flip(img_rgb, -1)  # -1 = Both axes

plt.figure(figsize=(10, 5))
plt.subplot(2, 2, 1), plt.imshow(img_rgb), plt.title("Original")
plt.axis("off")
plt.subplot(2, 2, 2), plt.imshow(img_flip_h), plt.title("Horizontal Flip")
plt.axis("off")
plt.subplot(2, 2, 3), plt.imshow(img_flip_v), plt.title("Vertical Flip")
plt.axis("off")
plt.subplot(2, 2, 4), plt.imshow(img_flip_hv), plt.title("Both Axes Flip")
plt.axis("off")
plt.show()

# -------------------------------------------------------------
# Step 7: Image Rotation (45° and 90° about center)
# -------------------------------------------------------------
center = (cols // 2, rows // 2)

M_rot_45 = cv2.getRotationMatrix2D(center, 45, 1.0)
img_rot_45 = cv2.warpAffine(img_rgb, M_rot_45, (cols, rows))

M_rot_90 = cv2.getRotationMatrix2D(center, 90, 1.0)
img_rot_90 = cv2.warpAffine(img_rgb, M_rot_90, (cols, rows))

plt.figure(figsize=(10, 4))
plt.subplot(1, 3, 1), plt.imshow(img_rgb), plt.title("Original")
plt.axis("off")
plt.subplot(1, 3, 2), plt.imshow(img_rot_45), plt.title("Rotated 45°")
plt.axis("off")
plt.subplot(1, 3, 3), plt.imshow(img_rot_90), plt.title("Rotated 90°")
plt.axis("off")
plt.show()
```

### Developed By:
**Name:** Santhosh K 

### Register No: 212225040379

---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed

- <img width="695" height="246" alt="image" src="https://github.com/user-attachments/assets/9d8a9579-1b54-4015-a004-34e91ca5f44c" />


### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed

- <img width="827" height="225" alt="image" src="https://github.com/user-attachments/assets/df53c9d9-0e65-44a0-9838-d1bf257c32c9" />


### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed

<img width="809" height="250" alt="image" src="https://github.com/user-attachments/assets/830d565a-dad4-4d0d-bd2c-b5210d3bc447" />

  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed

- <img width="651" height="576" alt="image" src="https://github.com/user-attachments/assets/1297cadc-a893-4dc8-a29e-1df454ef5ed8" />


### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  
<img width="850" height="207" alt="image" src="https://github.com/user-attachments/assets/ab386209-fe9b-4a0e-b9a5-cfd319bff967" />

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
