# Ex.05 Design a Website for Server Side Processing
## Date:03/12/2024

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
```
math.html
<meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Power Of A Lamp Filament In An Incandescent Bulb</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <style type="text/css">
        .edge {
            width: 1500px;
            margin-left: auto;
            margin-right: auto;
            padding-top: 300px;
            padding-left: 400px;
        }
        .box {
            display: red;
            border: thick dashed rgb(9, 151, 47);
            width: 550px;
            min-height: 350px;
            font-size: 25px;
            background-color: rgb(20, 185,70 );
        }
        .formelt {
            color: rgb(155, 8, 220);
            text-align: center;
            margin-top: 9px;
            margin-bottom: 8px;
        }
        h1 {
            text-align: center;
            padding-top: 25px;
        }
    </style>
</head>
<body>
    <div class="edge">
        <div class="box">
            <h1>Power Of A Lamp calculation</h1>
            M.krishna kumaran(24004032)
            <form method="POST">
               {% csrf_token %}
                <div class="formelt">
                    Intensity: <input type="text" name="intensity" value="{{ r }}"></input> amps<br/>
                </div>
                <div class="formelt">
                    Resistance: <input type="text" name="resistance" value="{{ h }}"></input>ohms<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br/>
                </div>
                <div class="formelt">
                    Power: <input type="text" name="power" value="{{ power }}" readonly></input> watts<br/>
                </div>
            </form>
        </div>
    </div>
</body>
</html>

views.py

from django.shortcuts import render 
def power(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = int(request.POST.get('intensity','0'))
        r = int(request.POST.get('resistance','0'))
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = i*i*r
        context['power'] = power
        context['i'] = i
        context['r'] = r
        print('Power=',power) 
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('power/',views.power,name="power"),
    path('',views.power,name="power")
]

```
## SERVER SIDE PROCESSING:
![alt text](<Screenshot (30).png>)


## HOMEPAGE:
![alt text](<Screenshot (31).png>)


## RESULT:
The program for performing server side processing is completed successfully.
