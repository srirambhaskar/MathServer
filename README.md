# Ex.05 Design a Website for Server Side Processing
## Date: 23-10-2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
```
mat.html
<html>
    <head>
        <title>Math</title>
        <style type="text/css">
            body{
                background-color: Greenyellow;
            }
            .edge{
                width: 80%;
                max-width: 1080px;
                padding-top: 30px;
                text-align: center;
            }
            .box{
                border: lightskyblue;
                width: 1200px;
                min-height: 300px;
                font-size: 20px;
                background-color: palevioletred;
                padding: 15px;
                box-sizing: border-box;
                display: inline-block;
            }
            .formeIt{
                color:deeppink;
                text-align: center;
                margin-top:5px;
                margin-bottom: 5px;
            }
            h1{
                color:darkorange;
                text-align: center;
                padding-top: 15px;
            }
        </style>
    </head>
    <body>
        <h1>Surface Area Calculator</h1>
        <h2 align="center">Developed by: Prajin S(212223230151)</h2>
        <div class="edge">
            <div class="box">
                <h1>Surface Area of Right Cylinder</h1>
                <form method="POST">
                    {% csrf_token %}
                    <div class="formeIt">
                        Radius of Cylinder : <input type="text" name="radius" value="{{r}}">(in metres)
                    </div>
                    <div class="formeIt">
                        Height of Cylinder : <input type="text" name="height" value="{{h}}">(in metres)
                    </div>
                    <div class="formeIt">
                        <input type="submit" value="Calculate">
                    </div>
                    <div class="formeIt">
                        Area of Cylinder : <input type="text" name="area" value="{{area}}">metre<sup>2</sup>
                    </div>
                </form>
            </div>
        </div>
    </body>
</html>
```
```
views.py
from django.shortcuts import render
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area =', area)
    
    return render(request, 'matapp/mat.html',context)
```
```
urls.py
from django.contrib import admin
from django.urls import path
from matapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfcaearea")
]
```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-04-18 131806.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-04-18 131733.png>)

## RESULT:
The program for performing server side processing is completed successfully.
