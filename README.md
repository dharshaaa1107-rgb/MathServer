# Ex.04 Design a Website for Server Side Processing
## Date:20\09\25

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

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

## PROGRAM:
math.html
```
<html>
<head>
    <title>Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: lightgrey;
            margin: 20px;
            padding: 20px;
            text-align: center;
        }

        h1 {
            color: darkblue;
        }

        form {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px grey;
            display: inline-block;
            margin: auto;
        }

        label {
            font-weight: bold;
            color: black;
        }

        input[type="number"] {
            padding: 5px;
            margin: 10px 0;
            border: 1px solid black;
            border-radius: 4px;
        }

        button {
            background-color: darkblue;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button:hover {
            background-color: navy;
        }
    </style>
</head>
<body>
    <h1>Power Calculator</h1>
    <form method="POST">
        {% csrf_token %}
        <label for="I">Enter Current (I in Amps):</label>
        <input type="number" name="intensity" id="I" value="{{ I }}" required>
        <br><br>
        <label for="R">Enter Resistance (R in Ohms):</label>
        <input type="number" name="resistance" id="R" value="{{ R }}" required>
        <br><br>
        <button type="submit">Calculate Power</button>
        <br><br>
        <label for="power">Calculated Power (Watts):</label>
        <input type="number" name="power" id="power" value="{{ power }}" readonly>
    </form>
</body>
</html>
```
views.py
```
from django.shortcuts import render 
def powercalc(request): 
    context={} 
    context['power'] = "0" 
    context['I'] = "0" 
    context['R'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        I = request.POST.get('intensity','0')
        R = request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',I) 
        print('resistance=',R) 
        power = (int(I) * int(I) ) * int(R) 
        context['power'] = power
        context['intensity'] = I
        context['resistance'] = R 
        print('power=',power) 
    return render(request,'mathapp/math.html',context)
```
urls.py
```
from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powercalculator/',views.powercalc,name="powercalculator"),
    path('',views.powercalc,name="powercalculatorroot")
]
```



## OUTPUT - SERVER SIDE:
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/32c67ef0-9871-41c3-9d0f-092db15be178" />


## OUTPUT - WEBPAGE:

<img width="1469" height="784" alt="image" src="https://github.com/user-attachments/assets/a673cf5e-889a-4894-8b22-e9e0f2817381" />

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
