# opencv-image-diff

Compare images using OpenCV library through its Java bindings

## Compile

Change OpenCV file jar location in file `build.properties` according to your OpenCV installation path.
Default is `/usr/local/share/OpenCV/java/opencv-300.jar`.

```
$ ant
```

This will comiple both executable and library jars. Look at `dist` folder.

## Executable

One can run executable jar with the following command:

```
$ java -cp /usr/local/share/OpenCV/java/opencv-300.jar:dist/opencv-image-diff-bin-0.1-201602201436.jar \
    -Djava.library.path=/usr/local/share/OpenCV/java/ \
    org.nebur.opencv.java.OpenCVImageDiff \
    -dd res/visu.jpg res/visu_1.jpg
```

Change paths `/usr/local/share/OpenCV/java/[...]` according to your OpenCV installation path.

### Options

Issue `-h` or `--help` to see command line arguments. 

Usage: [OPTIONS]... IMAGE1 IMAGE2

OPTIONS can be the following:

- **-a**, **--algorithm** - OpenCV algorithm to be used. Following OpenCV algorithms are supported:
  - **matchResult** (default)
    - IMAGE1 = template
    - IMAGE2 = test
  - **compareHist**
    - IMAGE1 = base
    - IMAGE2 = test
- **-m**, **--method** - OpenCV method of the specified algorithm. Available methods for each algorithm:
  - **matchResult**:
    - **CV_TM_SQDIFF**
    - **CV_TM_SQDIFF_NORMED**
    - **CV_TM_CCORR**
    - **CV_TM_CCORR_NORMED (default)**
    - **CV_TM_CCOEFF**
    - **CV_TM_CCOEFF_NORMED**
  - **compareHist**:
    - **CV_COMP_CORREL (default)**
    - **CV_COMP_CHISQR**
    - **CV_COMP_INTERSECT**
    - **CV_COMP_BHATTACHARYYA**
- **-t**, **--threshold** - Threshold used in diff comparisons
- **-e**, **--epsilon** - Epsilon used in diff comparisons: `(threshold - diff) > epsilon`
- **-dd**, **--display-diff** - Display on a graphical window the diff result
- **-mr**, **--merge-rects** - Merge error rectangles when display diff is enabled
- **-v**, **--verbose** - Improve output log

## Library

@TODO: doc library jar

## OpenCV

In order to better understand returned values and else take a look at:
  - Template Matching: http://docs.opencv.org/3.0.0/de/da9/tutorial_template_matching.html  
  - Histogram Comparison: http://docs.opencv.org/3.0.0/d8/dc8/tutorial_histogram_comparison.html
