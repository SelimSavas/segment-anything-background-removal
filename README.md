# Segment Anything Background Removal

I used Segment-Anything to remove background from photos. Doing this process is divided into two: 
* Foreground Detection and Segmentation
* Non-foreground(background) Removal

### Foreground Detection and Segmentation
* **Source Image :** Image entered by the user
* **Bounding Box Image :** User-entered bounding box
* **Segmented Image :** segmentation of the foreground image to be exempted from inference by segment anything

![image](https://user-images.githubusercontent.com/48186387/232865147-2fc7e7ed-aca5-497e-9a36-28dfaf057cc1.png)

### Background Removal

```
from PIL import Image

img = Image.fromarray(image_rgb)
mask = Image.open("/content/data/mask_2.png")
new_img = Image.new("RGBA", img.size, (0, 0, 0, 0))

for x in range(img.size[0]):
    for y in range(img.size[1]):
        if mask.getpixel((x,y)) == (255, 255, 255): # Beyaz piksel
            new_img.putpixel((x,y), img.getpixel((x,y)))
            
new_img.save("arkaplansiz_goruntu.png")
```

![image](https://user-images.githubusercontent.com/48186387/232865004-106676fb-a251-4a19-9ed2-dbb2f29810ff.png)
