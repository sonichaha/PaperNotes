1. crop：https://www.geeksforgeeks.org/python-pil-image-crop-method/
   ```
   yticklabels = [image.crop((0, index * image.size[1]/40, 1, index * image.size[1]/40 + 1)).resize((15, 15)) for index in yticks]
   ```
2. extent: https://matplotlib.org/stable/users/explain/artists/imshow_extent.html
    ````
    for i, label in enumerate(yticklabels):
            #add_image(axes[0], label, [-5, i])
            y = i + 1
            axes[0].imshow(label, extent=[-1, -0.2, i+0.1, y-0.1], aspect='auto')
    ````
