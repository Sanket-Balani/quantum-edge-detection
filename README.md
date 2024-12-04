## README for Quantum Edge Detection Project

Quantum Edge Detection: Exploring the potential of quantum computing for accelerated and improved image edge detection.

This project implements a Quantum Hadamard Edge Detection (QHED) algorithm for small images and explores its potential for larger images (32x32 pixels) and RGB images.

**Requirements**

* Python 3.x
* pip
* Qiskit framework (`pip install qiskit`)
* Pillow library (`pip install Pillow`)
* Matplotlib library (`pip install matplotlib`)

**Running the notebook**

1. Clone or download this repository.
2. Open a terminal or command prompt and navigate to the project directory.
3. Run the notebook using `Quantum_Edge_Detection.ipynb`.

**Explanation of the Code**

The notebook is divided into sections for processing small binary images, large binary images, and RGB images. Here's a breakdown of each section:

**1. Small Binary Image (8x8)**

* Defines a function `plot_image` to display the image using Matplotlib.
* Loads a sample 8x8 binary image as a NumPy array.
* Implements the Quantum Probability Image Encoding (QPIE) function:
    * Calculates the root mean square (RMS) of the image.
    * Normalizes the image pixel values by dividing each pixel by the RMS.
* Creates separate circuits for horizontal and vertical scans:

  Circuit for Horizontal Scan:
  
  ![image](https://github.com/user-attachments/assets/cade7f5d-fb13-4a5a-a1b5-3b169faf64bd)

  Circuit for Vertical Scan:
  
  ![image](https://github.com/user-attachments/assets/f26c45dc-2199-40e6-b6d7-d4f6160e5ba9)

    * Initializes the circuit with the normalized image coefficients.
    * Applies a Hadamard gate to the first qubit.
    * Applies a custom `Amp_permutation_unitary` matrix to shift the coefficients.
    * Applies another Hadamard gate to the first qubit.
* Simulates the circuits using the statevector simulator backend.
* Extracts the statevectors for both scans.
* Defines a thresholding function to convert amplitudes to binary values.
* Applies the thresholding function to the statevectors and reshapes them into images.
* Plots the original image, horizontal scan output, vertical scan output, and the combined edge-detected image.

**2. Large Binary Image (32x32)**

* Demonstrates processing a larger 32x32 binary image using the same principles as the small image section.
* Highlights the need for padding the image data to ensure a power of 2 size for efficient quantum circuit operations.

**Results**

![image](https://github.com/user-attachments/assets/d4e45559-31b0-4744-a7d7-26d84db2e3e3) ![image](https://github.com/user-attachments/assets/5fe3a961-4394-4034-91fc-e356b04b88f0)


**3. RGB Image (32x32)**

* Loads an RGB image using Pillow and resizes it to 32x32 pixels.
* Converts the RGB image to grayscale for edge detection.
* Applies the QPIE function to each color channel (red, green, blue) separately.
* Creates separate circuits for horizontal and vertical scans for each color channel.
* Combines the edge detection results from each color channel for the final output.

**Results**

![image](https://github.com/user-attachments/assets/8f229341-f89f-4d22-bd1f-1c54c50e6bfe) ![image](https://github.com/user-attachments/assets/4bd72105-4894-42e7-96a6-7ca88c6c7eb3)

![image](https://github.com/user-attachments/assets/338ebb01-ea0e-495e-a466-6ae0ee7f9af8) ![image](https://github.com/user-attachments/assets/a5869d8a-0196-4b01-917c-109571370fb2)


**Images**

The notebook includes comments indicating where the notebook expects to find the input images:

* `cat.png` (for large binary image demonstration)
* `Apple.jpg` (for RGB image demonstration, replace with your image path)
* `tree.jpg` (alternative RGB image demonstration, replace with your image path)

**Note:**

* This code demonstrates a basic implementation of QHED. Further optimization and exploration of different edge detection algorithms in the quantum domain are possible.
* The code uses a classical post-processing step for thresholding. Quantum thresholding techniques could be explored for a fully quantum approach.
