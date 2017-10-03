# PiCam-Project
##selfie
from picamera import PiCamera
from gpiozero import Button
from time import sleep

camera = PiCamera()
button = Button (17)

effects [
'none','negative','solarize','sketch',
'denoise','emboss','oilpaint','hatch',
'gpen','pastel','watercolor','film',
'blur','saturation','colorswap','washedout',
'posterise','colorpoint','colorbalance','cartoon',
'deinterlace1','deinterlace2'
]
    

camera.start_preview(alpha=192)

for i in range(22):
    camera.image_effect = 'emboss'
    camera.capture("/home/pi/image.jpg")
    
camera.stop_preview()
