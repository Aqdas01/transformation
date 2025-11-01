import cv2
import numpy as np
img = cv2.imread('photos/2.jpg')
cv2.imshow('img', img)

#resixing
resize = cv2.resize(img, (200,300))
cv2.imshow('resixe', resize)
#translation
def translate(resize , x, y):
    transMat = np.float32([[1,0,x], [0,1,y]])
    dimentions = (resize.shape[1], resize.shape[0])
    return cv2.warpAffine(resize, transMat, dimentions)
#-x ---left
#x---right
#y---up
#-y--down
translated = translate(resize, -100, -100)
cv2.imshow('translated',translated)
#rotation
def rotate(resize,angle,rotPoint = None):
    (height, width) = resize.shape[:2]
    rotMat = cv2.getRotationMatrix2D(rotPoint, angle,1.0)
    dimensions = (width, height)
    return cv2.warpAffine(resize, rotMat, dimensions)
rotated = rotate(resize, -45)
cv2.imshow('rotated', rotated)
rotated_rotated = rotate(rotated, -90)
cv2.imshow('rotated_rot', rotated_rotated)

cv2.waitKey(0)
