# pyhton-and-open-cv
import cv2
import numpy as np


video = cv2.VideoCapture("Green Screen Footage for test.mp4")
image = cv2.imread("HP-Hogwarts-39PHOTOBU17074_PHUP_HP.jpg")  


while True:
    ret, frame =  video.read()
    frame=cv2.resize(frame,(640,480))
    image =cv2.resize(image,(640,480))
    hsv=cv2.cvtColor(frame,cv2.COLOR_BGR2HSV)

    l_g=np.array([32,94,132])
    u_g=np.array([179,255,255])
 

    mask = cv2.inRange(hsv,l_g,u_g)
    res=cv2.bitwise_and(frame,frame,mask=mask)
    f=frame-res
    

 

