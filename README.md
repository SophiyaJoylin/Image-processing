# image-processing
Here’s how you can load an image, convert it to black and white, and then change it into a pencil sketch using Python
Step 1: Load Image and Convert to Black and White
We’ll use OpenCV for image processing. Make sure you have it installed by running:
code:
pip install opencv-python

Step 2: Convert Image to Black and White (Grayscale)
mport cv2

# Load the image
image = cv2.imread('path_to_your_image.jpg')
# Convert the image to grayscale (black and white)
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Save and show the grayscale image
cv2.imwrite('grayscale_image.jpg', gray_image)
cv2.imshow('Grayscale Image', gray_image)
cv2.waitKey(0)
cv2.destroyAllWindows()

Step 3: Convert Black and White Image into Pencil Sketch

# Invert the grayscale image
inverted_image = cv2.bitwise_not(gray_image)

# Apply GaussianBlur to the inverted image
blurred_image = cv2.GaussianBlur(inverted_image, (21, 21), 0)

# Invert the blurred image
inverted_blurred = cv2.bitwise_not(blurred_image)

# Create the pencil sketch by blending the grayscale and inverted blurred images
pencil_sketch = cv2.divide(gray_image, inverted_blurred, scale=256.0)

# Save and show the pencil sketch
cv2.imwrite('pencil_sketch.jpg', pencil_sketch)
cv2.imshow('Pencil Sketch', pencil_sketch)
cv2.waitKey(0)
cv2.destroyAllWindows()
Once the image is in grayscale, we can apply a pencil sketch effect

Explanation:

1. Grayscale: The original image is converted to black and white.

2. Inversion: We invert the grayscale image to create a negative version of it.

3. Blur: A Gaussian blur is applied to the inverted image to soften it.

4. Pencil Sketch: Finally, we divide the grayscale image by the blurred inverted image to create a pencil sketch effect
