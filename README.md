# 計算機圖學專案與實作

Implement the method in the paper with Python programming language and OpenCV library.
使用實作指定論文的方法。

## Color Transformer between Images
E. Reinhard, M. Ashikhmin, B. Gooch, and P. Shirley, “Color Transfer between Images,” IEEE Computer Graphics and Applications, vol. 21, no. 5, pp. 34-41, September/October 2001.

### Python Envioroment Installation
```
!pip install opencv-python
!pip install pandas
!pip install numpy
!pip install matplotlib
```

### Abstruct
One of the most common common tasks in image processing is to alter an images's color. Often this means removing a dominant and undesirable color cast, such as the yellow in photos taken under incandescent illumination. This article describes a method for a more general form of color correction that borrows one image’s color characteristics from another.

常見的圖片處理為轉換圖片的色彩，例如柔光特效、色彩覆蓋等。本論文提供一個可應用於所有圖片的方法，藉由使用另一張圖片的特徵，將指定圖片轉換為其他色彩。

### Method

- $S$: The image to be altered.
- $T$: The image which its characteristics to be used as a formula.
- $R$: The result of $S$.

1. Use OpenCV to read $S$ and $T$ as RGB images. RGB images represent as `numpy ndarray` with shape `(M, N, 3)`, `M` is height, `N` is width and `3` is RGB channels.
2. Calculate the standard deviation and the mean for each of color channels of $T$ and $S$.
3. Apply the formula $R(x, y) = d_t / d_s * [S(x, y) - m_s] + m_t$
    - $R(x, y)$: Pixel $(x, y)$ in $R$ in a channel.
    - $S(x, y)$: Pixel $(x, y)$ in $S$ in a channel.
    - $d_t$: Standard deviation in $T$ in a channel.
    - $d_s$: Standard deviation in $S$ in a channel.
    - $m_s$: Mean in $S$ in a channel.
    - $m_t$: Mean in $T$ in a channel.
4. Bound the values of channels into range 0 to 255, and output to $R$.

### Result
Source Image:

![](/source/01_kodim06.png)

Target Image:

![](/ttarget/01_kodim01.png)

Result Image:

![](/coltra/01_kodim06_kodim01.png)
