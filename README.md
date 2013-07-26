matplotlib-howto
================

## Step 1: Install matplotlib

Get it here: http://matplotlib.org/downloads.html

## Step 2: Get some data to plot

I used a python script that returned a 2-dimensional list, with the first index being all integers from 1 to 1,000,000 and the second being the integer's collatz-length.

```python

def collatz(n): #returns collatz-length of n
  i = 0
	steps_list = []
	while n != 1:
		if (n % 2 == 0):
			n = n / 2
			i+=1
			steps_list.append(n)
		else:
			n = (3 * n) + 1
			i+=1
			steps_list.append(n)
	return i

def steps_in_range(exclusive_end): # returns 2d list of integers and collatz-lengths
	number_steps_list = []
	for number in range(1, exclusive_end):
		total_steps = collatz(number,0)
		#						  x-coord, y-coord
		number_steps_list.append((number,total_steps))
	return number_steps_list  
```
`number_steps_list` is the actual list. It looks like this for 11 as the exclusive end:

```python
>>> step_in_range(11)
[(1, 0),(2, 1),(3, 7),(4, 2),(5, 5),(6, 8),(7, 16),(8, 3),(9, 19),(10, 6)]
```

## Step 3: Plot the data

First, pyplot needs to be imported from matplotlib:

```python
import matplotlib.pyplot as plt
```
Second, a plotting function needs to be written:
 
```python
def plotter():

  data = steps_in_range(100000001)

	X = [x for (x,y) in data]
	Y = [y for (x,y) in data]

	plt.plot(X,Y)
	plt.axis([0,1000,0,300])
	plt.xlabel( "Input Values" )
	plt.ylabel( "Steps to One" )
	plt.show()
```

This function will create a graph, with the x-coord being `data[index][0]` and y-coord being `data[index][1]`

`pyplot.axis` uses 4 arguments, [xmin, xmax, ymin, ymax]
`pyplot.[x | y]label` specify the text on the x and y axes.
`plt.show()` show the graph!

## Step 4: The finished product

All that led to this:

![alt text](http://i.imgur.com/lQwRC07.png "woah man")

There is a lot of stuff that can be messed with, like line styles, colors, etc.

## Step 5: Do more

Go here and learn more: http://matplotlib.org/users/pyplot_tutorial.html


