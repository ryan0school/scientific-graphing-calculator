# scientific-graphing-calculator
This Python script is a application allowing users to perform various math operations and graph plotting tasks. It provides three main functionalities: math, area, and graph plotting. 

My first two lines of code: (1) import matplotlib.pyplot as plt | (2) import numpy as np
These lines are important as they're necessary libraries for plotting graphs and numerical operations. Firstly, the 'matplotlib.pyplot' is used for creating and customizing plots while 'numpy' is a library supporting large, multi dimensional arrays, and matrices. Along with this is a large collection of high level math functions to operate on these arrays.

Next we have our function 'def get_float_input(prompt)':
This just prompts the user to enter a value.

while True:
This is a line which starts an infinite loop that will execute until it's explicity broken or the program terminates it.
try:
  user_input = float(input(prompt))
  return user_input
This block of code is inside the infite loops. The try statement is used to catch and handle the expections that may occur within the block.
The user_input is just prompting the user to input a number that is then converted into a value stored in the varaible user_input. The return user_input returns the input and breaks the infinite loop.

We now have the except ValueError:
  print("invalid input. please enter a valid number.")
This block of code is executed if a ValueError occurs within the try block. A ValueError is when the float function can't convert the user's input since they may have entered a string.

I put def calculate_linear_equation(m, c, x):
    return m * x + c
This line defines the function that takes three things -> the slope 'm' , the y-intercept 'c' , and the x-value 'x'
return m*x+c just calculates and returns the y-value of the linear equation 'y=mx+c'. 
More specifically it multiplies the slope by the x-value - (m*x) and adds the y-intercept (m*x+c). ex: y= 2x+3

After this is just the line where the user inputs whether they want to use my scientific graphing calculator for math, finding area, or graphing.
l = input("do you want: math, area, or graph: ")

Then I used if, elif, and else for each answer.
So I had given the input a variable 'l' so if they chose math it would run the code below the - if l == 'math'
If the user is to choose 'math' it prompts for two numbers and an operator (+.-,*,/). It also handles errors if someone were to input an invalid option.

Next we have the option if the user were to choose 'area'
This area is similar to the math option as we're just using if, elif, and else statements in the same way. It prompts for the shape (triangle, rectangle, square, and circle) and then prompts for the dimensions (base, height, length, width, side, or radius). It will then calculate and display the area based on the shape chosen.

After this we see the code for if the user selects 'graph'. The user will be prompted to choose between linear and polynomial, or trig graphs.
If the user is to choose 'linear and polynomial' they will be prompted to answer whether they want to include a linear equation by inputting yes, if not they will input no and get the polynomial graph alone.

If the user chose 'yes' it will prompt them for the slope (m) and y-intercept (c) of the linear equation as well as the polynomial eqution. It will then extract the coefficients and creates a 'numpy.poly1d' object representing the polynomial. It plots both the linear and polynomial equation on the same graph.

Coefficients and Intersection:
            try:
                coeffs = [float(c.split('*')[0]) if '*' in c else float(c) for c in e.split('+')]
                p = np.poly1d(coeffs[::-1])
                a, b, c = p.coeffs  

                if a != 0:
                    x_intersect = (c - b) / (2 * a)
                    y_intersect = a * x_intersect ** 2 + b * x_intersect + c
                    plt.scatter(x_intersect, y_intersect, color='red', label='Intersection')
                    print(f"Intersection point (x, y): ({x_intersect:.2f}, {y_intersect:.2f})")

                x = np.linspace(-10, 10, 400)
                y = np.polyval(coeffs[::-1], x)
So I had created a try statement which as I said before is to catch and handle exceptions that may occur within the block.
The first line 'coeffs = [float(c.split('*')[0]) if '*' in c else float(c) for c in e.split('+')] checks the polynomial equation entered by the user and extracts the coefficients. It splits the equation by the '+' operator and then extracts the coefficient from each term by splitting it by the '*' operator.  The coefficients are stored in the 'coeffs' list.

The second line 'p = np.poly1d(coeffs[::-1])' creates a numpy.poly1d object 'p' representing the polynomial equation with the coefficients in the coeffs list in reverse order.

The third line a, b, c = p.coeffs assumes that the polynomial equation is a quadratic equation and asings the coefficients a, b, c from the p.coeffs attributes.

The purpose of these three lines is to prepare the polynomial equation for further calculations and plotting. The numpt.ploy1d code evaluates the polynomial equation for different x-values.

Lastly we see how we find the intersection between the polynomial equation and the linear equation. 
On the first part of the code it checks if the coefficient 'a' of the polynomial equation is not zero. If a is zero it means the equation is not a quadratic equation.
Then it checks the x and y coordinates of the intersection point through the formula where is starts with the variables x_intersect and y_intersect.
These intersection points are then plotting on the graph using  plt.scatter(x_intersect, y_intersect, color='red', label='Intersection'). Then I set the colour of the plotted point to red. The coordinates are also printed at the end.

Next the code makes an array using np.linspace and evaluates the polynomial equation for x-values using np.polyval function storing the y-values in the 'y' variable. The coeffs[::1] part reverses the order of the coeeficients as since it's required by the np.polyval function. 

If the user selects trig graph it prompts them with choosing sin, cos, and tan. 
sin: makes array using np.linspace with values from 0, 2 * np.pi, 200. It calculates the sine of each value in 'x' and stores results in 'y'.
cos: generates the same 'x' arrray and calculates the cosine of each value storing results in 'y'
tan: same thing but calculates the tangent of each value and stores results in 'y'

Sources:
https://www.geeksforgeeks.org/numpy-poly1d-in-python/
https://www.w3schools.com/python/python_try_except.asp
https://www.w3schools.com/python/python_lists_comprehension.asp
https://www.w3schools.com/python/matplotlib_intro.asp
