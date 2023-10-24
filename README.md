# 8_Connectivity-labeled-Images
**Importing Libraries:**

•	The code imports essential libraries, including numpy for numerical operations and cv2 for computer vision tasks.
•	A random library is also imported to assign random colours to each labelled component.

**connectivity_8 Function:**

•	The connectivity_8 function is the main function that performs connectivity analysis and labelling. It takes an image file path as input and returns a color-coded labelled image.
•	The function uses an 8-connectivity approach, which considers the 8 neighbouring pixels when identifying connected components.

**Data Preparation:**

•	The input image is read in grayscale using cv2.imread, and its dimensions are obtained.
•	A binary mask (initially all zeros) is created to store the labels for connected components.
•	An equivalence table (equiv_table) and an ID counter (iD) are initialized for tracking connected components and their relationships.

**Helper Functions:**

Two helper functions are defined:
1.	get_parent: This function determines the parent/root label of a connected component by recursively following the equivalence table entries.
2.	connect_labels: This function connects two labels in the equivalence table.

**Pass 1: Labelling Connected Components:**

•	In this pass, the script iterates through the image, pixel by pixel.
•	For each pixel with a non-zero value (part of a connected component), it examines its neighbouring pixels and identifies the connected components already labelled.
•	If no neighbouring components are found, a new label is created (iD is incremented), and the pixel is assigned this label.
•	If neighbouring components are found, the pixel is assigned the minimum label from the neighbours, and equivalence relationships are updated using the connect_labels function.

**Pass 2: Resolving Equivalences:**

•	In this pass, the script iterates through the image again.
•	It resolves equivalence relationships by updating each label to its root parent.

**Colouring and Visualization:**

The script creates a colour image (RGB) to display the labelled components. A unique random color is assigned to each label.
Finally, the color-coded labelled image is returned.

**Main Execution:**

The code executes the connectivity_8 function with an input image 'img.bmp'. The resulting labelled image is displayed using OpenCV's cv2.imshow. The image is kept open until a key is pressed, after which it is closed using cv2.destroyAllWindows.
