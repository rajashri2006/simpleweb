# Ex.05 Design a Website for Server Side Processing
# Date:22-11-2024
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
HTML CODE
```
<html>
    <head>
        <title>app</title>
        <style>
            
            body{
                background-color: pink;
            }
            
            form{
                background-color: rgb(248, 231, 248)
            }
            .header{
                text-align: center;
                font-size: x-large;
            }
           
        </style>
    </head>
    <body>
        <div class="header">
        <h1>THE LAMP'S POWER</h1>
        </div>
        <form align ="center" method="post">
            {% csrf_token %}
            Intensity <input name="I" value="{{i}}">
            <br>
            <br>
            Resistance<input name="R" value="{{r}}">
            <br>
            <br>
            <input type="submit" value="calculate">
            <br>
            <br>
            Power<input name="power"value={{power}}>
        </form>
    </body>
</html>


```
VIEWS.PY
```
from django.shortcuts import render 
def lampspower(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('I','0')
        r = request.POST.get('R','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = (int(i)*int(i))*int(r) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r 
        print('Power=',power) 
    return render(request,'app1/math.html',context)

```
URLS.PY
```
from django.contrib import admin 
from django.urls import path 
from app1 import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('lampspower/',views.lampspower,name="lampspower"),
    path('',views.lampspower,name="lampspower")
]

```
# SERVER SIDE PROCESSING:
![IR TERMINAL](https://github.com/user-attachments/assets/e4504366-c49b-45db-a332-ee0cfb44415d)


# HOMEPAGE:

![IR input](https://github.com/user-attachments/assets/a685adaf-41b7-4b20-8d27-98a1819c7603)

 ![ir pink new](https://github.com/user-attachments/assets/25d61594-1625-4dcc-b5a3-371e183392d4)

# RESULT:
The program for performing server side processing is completed successfully.
