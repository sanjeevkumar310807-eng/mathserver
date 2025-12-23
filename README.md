# Ex.05 Design a Website for Server Side Processing
# Date:
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
````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Area of a Rectangle</title>
    <style>
        body {
            background-color: black;
            font-family: Arial, Helvetica, sans-serif;
        }

        .edge {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .box {
            width: 450px;
            background-color: rgb(32, 32, 32);
            border-radius: 10px;
            box-shadow: 0 0 10px rgb(255, 0, 179);
            padding-bottom: 20px;
        }

        h1 {
            color: rgb(255, 0, 179);
            text-align: center;
            padding-top: 20px;
        }

        .formelt {
            color: orange;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }

        input[type="text"] {
            padding: 5px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        input[type="submit"] {
            padding: 5px 15px;
            border-radius: 5px;
            border: none;
            background-color: rgb(255, 0, 179);
            color: white;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: rgb(200, 0, 140);
        }
    </style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Area of a Rectangle</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Length :
                <input type="text" name="length" value="{{l}}"> (in m)<br>
            </div>
            <div class="formelt">
                Breadth :
                <input type="text" name="breadth" value="{{b}}"> (in m)<br>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br>
            </div>
            <div class="formelt">
                Area :
                <input type="text" name="area" value="{{area}}"> m<sup>2</sup><br>
            </div>
        </form>
    </div>
</div>
</body>
</html>

views.py
from django.shortcuts import render
def rectarea(request):
    context = {}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')
        print('request :', request)
        print('Length :', l)
        print('Breadth :', b)

        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area :', area)
    return render(request, 'mathapp/math.html', context)

urls.py
rom django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [ 
    path('admin/', admin.site.urls),
    path('', views.rectarea, name="areaofrectangleroot")
]
````
# SERVER SIDE PROCESSING:
<img width="1884" height="952" alt="processing" src="https://github.com/user-attachments/assets/042a1345-393d-451a-8085-89ab4f76dec6" />


# HOMEPAGE:
<img width="1877" height="910" alt="output" src="https://github.com/user-attachments/assets/cf946edc-2273-4cf7-91bf-0982da4e3925" />

# RESULT:
The program for performing server side processing is completed successfully.
