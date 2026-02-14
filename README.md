Netpbm Image Processing Engine

This project is a high-performance command-line image processing engine written in C. It is designed to manipulate Netpbm image formats (P1, P2, and P3) - text files, supporting both grayscale and RGB color spaces.
The program emphasizes manual memory management, pointer arithmetic, and algorithmic efficiency in spatial domain image processing.
The system implements a command-line interface for real-time interaction, allowing users to perform complex transformations, statistical analysis, and convolutional filtering on specific Regions of Interest.

 
Core Features
1. Format Support and I/O
Netpbm Compatibility: Full support for P1 (Black and White), P2 (Grayscale), and P3 (RGB) text-based formats.
Dynamic Parsing: Custom parser designed to handle metadata and skip comments (#) during the header reading phase.
Persistence: Standardized SAVE functionality that preserves the current state of the image to the local filesystem.

2. Spatial Domain Transformations
Selection Management: Implementation of coordinate-based selection (x1, y1, x2, y2).
Includes automatic coordinate ordering to ensure robustness against user input errors. 
Image Cropping: Efficient sub-matrix extraction by reallocating memory and re-mapping pixel data to a new reduced-dimension grid.
Rotation Logic: Supports +-90 degrees, +-180 degrees, +-270 degrees and +-360 degrees rotations. The algorithm utilizes matrix transposition and reversal techniques to perform 90 degrees clockwise increments.

3. Image Enhancement and Filtering
Convolutional Kernels: Implementation of a 3 x 3 sliding window convolution engine.
Edge Detection: High-pass filter highlighting intensity discontinuities.
Sharpen: Enhances high-frequency components.
Blur & Gaussian Blur: Low-pass filtering for noise reduction and smoothing.
Automatic Clamping: A dedicated clamp() function ensures all pixel values remain within the valid [0, 255] range, preventing integer overflow/underflow after kernel application.

4. Statistical Analysis
Histogram Generation: Calculates pixel frequency distribution across Y bins (where Y is a power of 2).
Histogram Equalization: Enhances image contrast by linearizing the Cumulative Distribution Function of the grayscale intensity levels.
