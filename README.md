import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
import os
path
classes = {'no_tumor':0, 'pituitary_tumor':1}
import
X = []
Y = []
for cls in classes:
 pth = +
 for j in os.listdir(pth):
 img = cv2.imread(pth+'/'+j,0)
 img = cv2.resize(img, (200, 200))
 X.append(img)
 Y.append(classes[cls])
 np.unique(Y)
X = np.array(X)
Y = np.array(Y)
pd.Series(Y).value_counts()
X.shape
plt.imshow(X[0], cmap='gray')
X_updated = X.reshape(len(X), -1)
X_updated.shape
xtrain, xtest, ytrain, ytest = train_test_split(X_updated, Y, random_state=10, test_size=.20
xtrain.shape, xtest.shape
print(xtrain.max(), xtrain.min())
print(xtest.max(), xtest.min())
xtrain = xtrain/255
xtest = xtest/255
print(xtrain.max(), xtrain.min())
print(xtest.max(), xtest.min())from sklearn.decomposition import PCA
print(xtrain.shape, xtest.shape)
pca = PCA(.98)
pca_train = xtrain
pca_test = xtest
from sklearn.linear_model import LogisticRegression
from sklearn.svm import SVC
import warnings
warnings.filterwarnings('ignore')
lg = LogisticRegression(C=0.1)
lg.fit(pca_train, ytrain)
sv = SVC()
sv.fit(pca_train, ytrain)
print("Training Score:", lg.score(pca_train, ytrain))
print("Testing Score:", lg.score(pca_test, ytest))
print("Training Score:", sv.score(pca_train, ytrain))
print("Testing Score:", sv.score(pca_test, ytest))
pred = sv.predict(pca_test)
np.where(ytest != pred)
pred[36]
ytest[36]
dec = {0:'No Tumor', 1:'Positive Tumor'}
plt.figure(figsize=(12,8))
p =
c=1
for i in
 plt.subplot(3,3,c)
 
 = cv2.imread(
 img1 = cv2.resize(img, (200,200))
 img1 = img1.reshape(1,-1)/255
 p = sv.predict(img1)
 plt.title(dec[p[0]])
 plt.imshow(img, cmap='gray')
 plt.axis('off')
 c+=1
 plt.figure(figsize=(12,8))
p =
c=1
 plt.subplot(4,4,c)
 
 
 img1 = cv2.resize(img, (200,200))
 img1 = img1.reshape(1,-1)/255
 p = sv.predict(img1)
 plt.title(dec[p[0]])
 plt.imshow(img, cmap='gray')
 plt.axis('off')
 c+=1
p=os.listdir('C:sohan/project/Brain Tumor Detection Classification/Testing/pi')
for i in os.listdir('C:/sohan/project/Brain Tumor Detection Classification/Testing/pi')
img = cv2.imread('C:/sohan/project/Brain Tumor Detection Classification/Testing/pi')
 img1 = cv2.resize(img, (200,200))
img1 = img1.reshape(1,-1)/255
 p = sv.predict(img1)
 plt.title(dec[p[0]])
 plt.imshow(img, cmap='gray')
 plt.axis('off')
 c+=1

