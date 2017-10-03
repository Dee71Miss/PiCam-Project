##selfie
from picamera import PiCamera
from gpiozero import Button
from time import sleep
import subprocess
import image

camera = PiCamera()
button = Button (17)

effects = [
'none','negative','sketch',
'denoise','emboss','oilpaint','hatch', 'pastel','watercolor','colorswap','washedout',
'posterise','colorbalance','cartoon',
'deinterlace1','deinterlace2'
]
camera.start_preview(alpha=192)
button.wait_for_press()

for i in range(16):
    camera.image_effect = effects[i]
    camera.capture("/home/pi/pic_{0}.png".format(i))
    
camera.stop_preview()

command = "montage pic_0.png pic_1.png pic_2.png pic_3.png pic_4.png pic_5.png pic_6.png pic_7.png pic_8.png pic_9.png pic_10.png pic_11.png pic_12.png pic_13.png pic_14.png pic_15.png-tile 4x -geometry 480x480 +4+4  tile.png"
process = subprocess.Popen(command.split(), stdout=subprocess.PIPE)
output, error = process.communicate()
