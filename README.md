# Daily Photo Capture and Color Analysis README

This project consists of two main parts:

1. A script that uses a camera module to take a photo every day at 9am for a year.
2. A script that analyses all the images in a specific folder to find the CMYK value of the most prominent color in each image and writes these values to a text file.

## Part 1: Daily Photo Capture

This script uses the `schedule` and `picamera` modules in Python to take a picture every day at a specified time. The photos are stored in a designated directory.

### Dependencies

- Python 3
- picamera
- schedule

You can install these packages using pip:

```bash
pip install picamera schedule
```

### How to Run the Script

Set up the script to run automatically when your system starts. The method depends on your operating system. Replace '/path/to/save/image/' with the directory where you want to save the images. 

```python
camera.capture('/path/to/save/image/{}.jpg'.format(timestamp))
```

### Output

The script will save images to the specified directory. Each image will be saved with a timestamp in the format `YYYY-MM-DD_HH-MM-SS`.

## Part 2: Most Prominent Color Finder

This script loads each image from the specified directory, performs a K-means clustering operation to find the most prominent color, converts this color from RGB to CMYK, and writes the filename and corresponding CMYK value to an output file.

### Dependencies

- Python 3
- OpenCV
- scikit-learn
- scikit-image

You can install these packages using pip:

```bash
pip install opencv-python sklearn scikit-image
```

### How to Run the Script

Replace `'path_to_your_folder'` with the directory that contains the images you want to analyze. Also replace `'output.txt'` with the path where you want to write the output file.

```python
iterate_folder_and_save_to_file('path_to_your_folder', 'output.txt')
```

### Output

The script will generate a text file with each line in the format: `filename: [c, m, y, k]`, where `c`, `m`, `y` and `k` are the CMYK values of the most prominent color in the respective image.

### Limitations and Considerations

The color analysis script uses a simple version of the K-means clustering algorithm, which assumes the most prominent color is the one with the most pixels. Depending on the image, a more advanced color prominence algorithm may be more suitable.
