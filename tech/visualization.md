# Visualization 

## templates (matplotlib, seaborn, bokeh)
- matplotlib & seaborn examples https://github.com/er1czz/data_challenge_insight/blob/main/5_CreditCard_userSegmentation.ipynb
- Bokeh tutorial https://github.com/er1czz/Bokeh_tutorial

## Display an resized image in Jupyter Notebook
```
def show_img(img_name = 'xyz.png'):
    from PIL import Image
    
    path = f'groundtruth_p1/' + img_name
    img = Image.open(path)
    
    # resize to fixed width 300 pixels
    width, height = img.size
    ratio = height/width
    newwidth = 300
    newheight = int(ratio * newwidth)
    img = img.resize((newwidth, newheight), Image.ANTIALIAS) 
    ##
  
    display(img)
```
