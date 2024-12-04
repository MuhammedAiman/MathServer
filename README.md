# Ex.05 Design a Website for Server Side Processing
## Date:04/12/2024

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
math.html

{% load static %}
<html>
<head>
    <title>math</title>
    <style>
        
h1{
    border: 2px solid ;
    padding: 25px;
    margin: 15px;
    border-radius: 10px;
    position: fixed;
    top: 200px;
    left: 615px;
    font-size: xx-large;
    font-weight: bolder;
    font-variant: small-caps;
    background: palegreen;
    font-family: Georgia;
    color: black;
}
form{
    border: 2px solid pink;
    background-color:palevioletred ;
    padding: 30px;
    margin: 10px;
    border-radius: 10px;
    width: 425px;
    position: fixed;
    top: 300px;
    left: 527px;
    
}

    </style>
</head>
<body bgcolor="paleturquoise">
    <h1 align="center" > Power Of Lamp </h1>
    <form align="center" method="POST">
    {%csrf_token%}
     
    <div class="power">

        <label>"INTENSITY"</label>
        <input type="text" name="intensity" value="{{i}}">
    </div>
    <br>
    <div class="power">
        <labe>"RESISTANCE"</label>
        <input type="text" name="resistance" value="{{r}}">
    </div>
    <br>
    <input type="submit" value="CALCULATE">
    <br>
    <br>
    <div class="power">
        <label>"POWER"</label>
        <input type="text" name="POWER" value="{{power}}">
        
    </div>
</form>
</body>
</html>

views.py

from django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'myapp/math.html',context)

urls.py

from django.contrib import admin 
from django.urls import path 
from myapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
]

## SERVER SIDE PROCESSING:
![alt text](<Screenshot (20).png>)

## HOMEPAGE:

![alt text](<Screenshot (18).png>)
## RESULT:
The program for performing server side processing is completed successfully.
