# Unsupervised Change Detection in Multi-Temporal Satellite Images using PCA & K-Means

Automatic change detection in images of the same region taken at different times is a fascinating topic in image processing. These images, known as multi-temporal images, are analyzed to identify any changes that have occurred between two timestamps. Change detection is a vital application of remote sensing, with uses spanning defense inspections, deforestation monitoring, land use analysis, disaster assessment, and tracking various environmental or human-induced changes.

In this experiment, we’ll outline an unsupervised approach to change detection. The method focuses on the automatic analysis of the difference image, which is generated by subtracting two multi-temporal images on a pixel-by-pixel basis. Principal Component Analysis (PCA) is then applied to extract Eigen vectors from pixel blocks in the difference image. Using these Eigen vectors, we construct a feature vector for each pixel by projecting its neighborhood onto the Eigen vector space. These feature vectors collectively form a feature vector space (FVS). Clustering this FVS using the K-means algorithm creates two clusters: one for pixels representing changes and the other for pixels with no changes. Each pixel is assigned to one of these clusters, resulting in a change map.

The steps to implement this method are as follows:

1. Generate the difference image and Eigen vector space (EVS).
2. Build the feature vector space (FVS).
3. Cluster the feature vector space and create the change map.

## Features
- Change detection between two time periods
- Principal Component Analysis (PCA) for feature reduction
- K-means clustering for change pattern identification
- Saving Visualization of results

## Requirements

```
numpy
opencv-python
imageio
collections
scikit-learn
```

## Input Data

The code expects two satellite images:
- `before.png`: Satellite image from the earlier time period
- `after.png`: Satellite image from the later time period

Images should be in either png or jpg format. We can tweak code to support GEOTIFF format.

## Output

The code generates several visualizations:
1. difference map
2. change map
3. cleaned change map

Output files:
- `changemap.jpg`: Binary change mask
- `cleanchangemap.jpg`: Cleaned version of binary change mask
- `diff.jpg`: Visualization of image difference

## Usage

1. Place your satellite images in the `data` directory
2. Run the script:
```bash
python main.py
```

## Analysis Components

1. **Difference Image Generation**
   - Computes the difference image by performing pixel-by-pixel subtraction between the two multi-temporal satellite images.
   - Highlights areas of potential change, where significant differences in pixel intensity indicate altered regions.

2. **PCA Analysis**
   - Applies Principal Component Analysis (PCA) to the difference image to extract Eigen vectors from pixel blocks.
   - Reduces data dimensionality and identifies dominant patterns of variation in the difference image.

3. **Feature Vector Construction**
   - Projects each pixel’s neighborhood onto the Eigen vector space to create a feature vector for every pixel.
   - Constructs the feature vector space (FVS) as a collection of feature vectors for all pixels.

4. **K-means Clustering**
   - Groups the pixels into two clusters using the K-means algorithm.
   - One cluster represents unchanged areas, and the other corresponds to changed areas.
   - Produces a binary change map based on cluster assignments.

## Visualization Guide
- `Difference Map`:
   - Visualizes pixel intensity differences between the two images.
   - Bright areas indicate significant changes, while darker areas signify minimal changes.

- `Change Map`:
   - Binary map showing changed (white) and unchanged (black) regions.

- `Cleaned Change Map`:
   - Post-processed version of the change map to remove noise and refine boundaries.