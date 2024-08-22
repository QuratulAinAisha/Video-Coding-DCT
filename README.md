# DCT and iDCT on YUV Video Sequences

This project implements the Discrete Cosine Transform (DCT) and its inverse (iDCT) on a YUV video sequence to compress and then reconstruct the video frames. The code applies quantization, dequantization, and inverse DCT on each 8x8 block of a YUV frame. The resulting reconstructed frames are saved back into a YUV video file.

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Code Structure](#code-structure)
7. [Quantization Table](#quantization-table)


## Introduction

In image and video compression, the Discrete Cosine Transform (DCT) is used to convert the spatial representation of video frames into frequency components, which are easier to compress. In this project, the Y (luminance) channel of YUV video sequences is processed using DCT. Quantization is applied to reduce the amount of information by discarding less significant frequency components, followed by inverse quantization and iDCT to reconstruct the frames. The project demonstrates basic video compression techniques and their effect on the reconstructed video quality.

## Features

- **DCT and iDCT**: Performs 2D DCT on each 8x8 block of the Y (luminance) channel of YUV frames and reconstructs the video by applying iDCT.
- **Quantization and Inverse Quantization**: Applies quantization to DCT coefficients and performs dequantization during reconstruction.
- **Reconstruction**: Rebuilds the video frames from compressed data and saves the results to a new YUV file.

## Requirements

- **Python 3.x**
- **NumPy** for numerical operations
- **Matplotlib** for plotting original and reconstructed frames (optional for visualization)

## Installation

To install the required dependencies, run the following command:

```bash
pip install numpy matplotlib
```

## Usage

1. Ensure you have a YUV video file in the correct location. Update the `filename`, `width`, and `height` parameters in the code to match your video sequence.

2. Run the script to perform DCT, quantization, and iDCT on the Y channel of the YUV video. The reconstructed frames will be saved in a new YUV file.

   ```bash
   python DCT_yuv.py
   ```

3. The output file will be saved as `reconstructedForeman.yuv` in the working directory.

## Code Structure

### `performDCT_2D`

This function computes the 2D DCT for an 8x8 block of the input frame using the following formula:

```python
def performDCT_2D(f):
    # Computes the 2D Discrete Cosine Transform (DCT) on an 8x8 block.
```

### `iDCT_2d`

This function computes the inverse 2D DCT for an 8x8 block:

```python
def iDCT_2d(F):
    # Computes the inverse 2D Discrete Cosine Transform (iDCT) on an 8x8 block.
```

### `read_yuv_frames`

Reads YUV video frames and extracts the Y (luminance) channel:

```python
def read_yuv_frames(filename, width, height):
    # Reads YUV frames from the file and returns a list of Y channel frames.
```

### `apply_quantization` and `apply_inverse_quantization`

Applies quantization to the DCT coefficients and then inverse quantization during reconstruction:

```python
def apply_quantization(F, Q):
    # Applies quantization to the DCT coefficients.

def apply_inverse_quantization(quantized_F, Q):
    # Applies inverse quantization to the quantized coefficients.
```

### `main`

The `main` function performs the following:
- Reads the YUV video sequence and extracts Y channel frames.
- Applies DCT and iDCT block-by-block.
- Saves the reconstructed frames back into a YUV video file.

```python
def main():
    # Executes the main flow of DCT, quantization, iDCT, and reconstruction.
```

## Quantization Table

The quantization table `Q` is used to compress the DCT coefficients. This reduces the amount of data stored for each block, focusing on more significant frequency components:

```python
Q = [[16, 11, 10, 16, 24, 40, 51, 61],
     [12, 12, 14, 19, 26, 58, 60, 55],
     [14, 13, 16, 24, 40, 57, 69, 56],
     [14, 17, 22, 29, 51, 87, 80, 62],
     [18, 22, 37, 56, 68, 109, 103, 77],
     [24, 35, 55, 64, 81, 104, 113, 92],
     [49, 64, 78, 87, 103, 121, 120, 101],
     [72, 92, 95, 98, 112, 100, 103, 99]]
```


When you run the script, it processes each 8x8 block of the input video frames by performing DCT, quantization, dequantization, and iDCT. The reconstructed frames are stored in a new YUV file named `reconstructedForeman.yuv`.

In addition, the script displays the original frame, DCT coefficients, and the reconstructed frame for visualization purposes. This allows you to observe the effect of the DCT-based compression and reconstruction.

Output frames:
- **Original Frame**: Displayed in grayscale.
- **DCT Coefficients**: Visualization of the frequency components.
- **Reconstructed Frame**: The frame after applying iDCT, showcasing how much of the original data is retained after compression.

