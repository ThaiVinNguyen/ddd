# Project-1-Search-and-Sample-Return
```python
def color_thresh(img, rgb_thresh=(160, 160, 160,100,100,50)):
    # Create an array of zeros same xy size as img, but single channel
    color_select_path = np.zeros_like(img[:,:,0])
    color_select_rock = np.zeros_like(img[:,:,0])
    color_select_obstacle = np.zeros_like(img[:,:,0])
    # Require that each pixel be above all three threshold values in RGB
    # above_thresh will now contain a boolean array with "True"
    # where threshold was met
    # Threshold for terrain path
    above_thresh = (img[:,:,0] > rgb_thresh[0]) \
                & (img[:,:,1] > rgb_thresh[1]) \
                & (img[:,:,2] > rgb_thresh[2])
    # Threshold for rocks
    between_thresh = (img[:,:,0] > rgb_thresh[3] ) \
                & (img[:,:,1] > rgb_thresh[4] ) \
                & (img[:,:,2] < rgb_thresh[5] )
    # Threshold for obstacles
    below_thresh = (img[:,:,0] < rgb_thresh[0]) \
                & (img[:,:,1] < rgb_thresh[1]) \
                & (img[:,:,2] < rgb_thresh[2])
    # Index the array of zeros with the boolean array and set to 1
    color_select_path[above_thresh] = 1
    color_select_rock[between_thresh] = 1
    color_select_obstacle[below_thresh] = 1
    # Return the binary image
    return color_select_path, color_select_rock, color_select_obstacle
threshed_path, threshed_rock, threshed_obstacle = color_thresh(warped)
threshed_obs = np.absolute(np.float32(threshed_obs))*mask
fig = plt.figure(figsize=(12,9))
plt.subplot(221)
plt.imshow(threshed_path,cmap='gray')
plt.subplot(222)
plt.imshow(threshed_rock,cmap='gray')
plt.subplot(223)
plt.imshow(threshed_obs, cmap='gray')
#scipy.misc.imsave('../output/warped_threshed.jpg', threshed*255)
```
