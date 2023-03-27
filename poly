from sympy import *
import numpy as np 
import copy

class Poly():

  def __init__(self,poly_coeff):
    self.coefficients=[]
    self.coefficients=poly_coeff

  def get_note(self):
    note=[]
    if self.coefficients[0]!=0:
      note+=str(self.coefficients[0])+"+"
    if self.coefficients[1]!=0:
      if self.coefficients[1]!=1:
        note+=str(self.coefficients[1])+"x+"
      else:
        note+="x+"

    for i in range (2,len(self.coefficients)):
      if self.coefficients[i] !=0 and self.coefficients[i]!=1:
        note+=str(self.coefficients[i])+"x^"+str(i)+"+"
      elif self.coefficients[i] ==1:
        note+="x^"+str(i)+"+"

    for i in range(len(note)-1):
      print(note[i], end="")
    return note  

  def value(self,coordinates):
    c=0
    len1=len(self.coefficients)
    len2=len(coordinates)
    if len1>len2: 
      for i in range(len1-len2):
        coordinates.append(0)
      for i in range(len1):
        c+=(self.coefficients[i]*coordinates[i])
    if len2>len1: 
      for i in range(len2-len1):
        self.coefficients.append(0) 
      for i in range(len2):
        c+=(self.coefficients[i]*coordinates[i])
    return c 


  def add(self,  poly2):
    c=[]
    len1=len(self.coefficients)
    len2=len(poly2.coefficients)

    if len1>len2: 
      for i in range(len1-len2):
        poly2.coefficients.append(0)
      for i in range(len1):
        c.append(self.coefficients[i]+poly2.coefficients[i])
    if len2>len1: 
      for i in range(len2-len1):
        self.coefficients.append(0)  

      for i in range(len2):
        c.append(self.coefficients[i]+poly2.coefficients[i])
        self.coefficients[i]=c[i]
    self.get_note()
   
  def difference(self, poly2,poly1):
    c=[]
    len1=len(poly1.coefficients)
    len2=len(poly2.coefficients)

    if len1>len2: 
      for i in range(len1-len2):
        poly2.coefficients.append(0)
      for i in range(len1):
        c.append(poly1.coefficients[i]-poly2.coefficients[i])
    if len2>len1: 
      for i in range(len2-len1):
        poly1.coefficients.append(0)  

      for i in range(len2):
        c.append(poly1.coefficients[i]-poly2.coefficients[i])
        poly1.coefficients[i]=c[i]
    poly1.get_note()
    return poly1.coefficients
  

  def divmod(self, poly1, poly2):
    len1=len(poly1.coefficients)
    len2=len(poly2.coefficients)
    c=self
    for i in range(len1-len2+1):
      c.coefficients[i]=0
    
    rat=0.0
    rem=poly1
    j=len1-1
    if(len1<len2):
      rat=0
      rem.coefficients=poly1.coefficients
    else:
      while(j>=len2):
        
        rat=rem.coefficients[j]/poly2.coefficients[len2-1]
        c.coefficients[j-len2+1]=rat
        rem.coefficients=poly1.difference(rem,poly1.multiply(c,poly2))
        print(rem.coefficients)
        j-=1

    print(c.coefficients)
    print(rem.coefficients)


  def multiply(self,poly1, poly2):

    len1=len(poly1.coefficients)
    len2=len(poly2.coefficients)
     
    index_array=np.zeros(len1+len2)
    
    for i in range(len1):
      for j in range(len2):
       
        index_array[i+j]+=poly1.coefficients[i]*poly2.coefficients[j]
    
    if len(poly1.coefficients)<len(index_array):
      for i in range(len(index_array)-len(poly1.coefficients)):
       poly1.coefficients=np.append(poly1.coefficients,0)
      for i in range(len(index_array)):
       poly1.coefficients[i]=index_array[i]
    poly1.coefficients=index_array
    #return self.coefficients
    poly1.get_note()
     
  def power(self,k,poly):
    d=copy.deepcopy(poly)
    c=copy.deepcopy(poly)
    for i in range(k-1):
      poly.multiply(poly,d)
    #return poly.coefficients

x_coeff=[1,1]
x=Poly(x_coeff)
d=copy.deepcopy(x)

print("\n")
x.get_note()
print("\n")
y_coeff=[1,1,4,5]
y=Poly(y_coeff)
x.multiply(x,y)
print("\n\n")

print(d.power(4,d))

x=Poly([11,11,11])
y=Poly([11,11,11])
x.divmod(x,y)
