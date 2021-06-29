# Blurring-Image

from PIL import Image
import matplotlib.pyplot as plt
import numpy as np

im = Image.open("../BNL Week 3/city.jpeg")
arr = np.array(im, dtype="uint16")[:, :, 0]
plt.imshow(arr, cmap="gray", vmin=0, vmax=255)
plt.show()

height, width = arr.shape
blurr = np.zeros((height, width))

for i in range(1, height - 1):
    sum = 0
    for j in range(1, width - 1):  
        sum = (arr[i][j] + arr[i-1, j] + arr[i+1, j] + arr[i, j-1] + arr[i, j+1] + arr[i-1, j-1] + arr[i-1, j+1] + arr[i+1, j-1] + arr[i+1, j+1]) // 9
    blurr[i][j] = arr[i][j]


plt.imshow(blurr, cmap="gray", vmin=0, vmax=255)
plt.show()
