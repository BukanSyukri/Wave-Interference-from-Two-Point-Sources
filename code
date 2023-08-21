import numpy as np
import matplotlib.pyplot as plt
from ipywidgets import interactive

#Axis
L0 , L1 = 0, 10 #Lower limit and upper limit of x-axis
y0, y1 = -10, 10 #Lower limit and upper limit of y-axis
x_p, y_p = 150, 150 #Points in x- and y-axis
x = np.linspace(L0, L1, x_p) #x-axis
y = np.linspace(y0, y1, y_p) #y-axis
X, Y = np.meshgrid(x, y, sparse=False) #Create rectangular matrix/grid for x and y 
points = np.concatenate([X.reshape(-1,1), Y.reshape(-1,1)], axis=-1) #Connect x and y axis 

def fx(k,a,E01,E02):
  #Position of slits (in cm)
  s1 = np.array([0, a/2]) #Position of first slit
  s2 = np.array([0, -a/2]) #Position of second slit
  S1 = points - s1 #An array of changes in x and y for first slit
  S2 = points - s2 #An array of changes in x and y for second slit
  print("Position of first slit:", s1[1], "cm on y-axis")
  print("Position of second slit:", s2[1], "cm on y-axis")
  
  #Calculation
  x1 = np.sqrt((S1[:, 0]**2)+(S1[:, 1]**2)) #Radius of wave from first slit
  x2 = np.sqrt((S2[:, 0]**2)+(S2[:, 1]**2)) #Radius of wave from second slit
  E1 = E01*np.sin(k*x1) #Electric field of wave from first slit
  E2 = E02*np.sin(k*x2) #Electic field of wave from second slit
  E = E1 + E2 #Resultant electric field 
  I = E**2 #Irradiance
  
  #Plotting
  plt.figure(figsize=(5,5)) #Size of the output figure
  plt.xlim(L0,L1) #Limit for x-axis
  plt.ylim(y0,y1) #Limit for y-axis
  plt.scatter(points[:,0],points[:,1], c=I) #Points for intensity of wave interference
  plt.scatter(*s1, c='yellow') #Point for first slit
  plt.scatter(*s2, c='yellow') #Point for second slit
  plt.show()

#Slider
interactive(fx,k=(0,10,1),a=(0,5,0.1),E01=(0,5,0.1),E02=(0,5,0.1))
