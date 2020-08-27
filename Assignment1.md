##Assignment 1

1. Write a function with the following signature: pythagoreanTheorem(length_a, length_b)
```python
from math import sqrt

def pythagoreanTheorem(side_a, side_b):
    return sqrt(side_a * side_a + side_b * side_b)


a = int(input('Length of side a: '))
b = int(input('Length of side b: '))
side_c = pythagoreanTheorem(a, b)
print('Length of side c:' + str(side_c))

```
The output for the above code is as follows:
```
#output 1:
  Length of side a: 5
  Length of side b: 3
  Length of side c:5.830951894845301

  #output 2:
  Length of side a: 2
  Length of side b: 9
  Length of side c:9.219544457292887

  #output 3:
  Length of side a: 4
  Length of side b: 3
  Length of side c:5.0
```

2. Write a function with the following signature: list_mangler(list_in).

    To check if the element is even, we mod the value of the element with 2 and if the result is 0, the number is even. If the number is even, we multiply the value by 2 else we multiply it by 3.

The code for above is:
```python
def list_mangler(list_in):
    new_list = []
    for x in range(0, len(list_in)):
        if list_in[x] % 2 == 0:
            new_list.append(list_in[x] * 2)
        else:
            new_list.append(list_in[x] * 3)

    return new_list


list1 = [13, 2, 32, 41]
print('List 1:' + str(list1))
print('Output of List 1:'+str(list_mangler(list1)))
list2 = [2, 8, 16, 32]
print('List 2:' + str(list2))
print('Output of List 2:'+str(list_mangler(list2)))
list3 = [11, 21, 31, 41, 51]
print('List 3:' + str(list3))
print('Output of List 3:'+str(list_mangler(list3)))
```
The output for the code above is as follows:
```
List 1:[13, 2, 32, 41]
Output of List 1:[39, 4, 64, 123]
List 2:[2, 8, 16, 32]
Output of List 2:[4, 16, 32, 64]
List 3:[11, 21, 31, 41, 51]
Output of List 3:[33, 63, 93, 123, 153]
```

3. Write a function with the following signature: grade_calc(grades_in, to_drop).
```python
def grade_calc(grades_in, to_drop):
    # dropped lowest values
    listVal = len(sorted(grades_in, reverse=True)) - int(to_drop)
    average = sum(sorted(grades_in, reverse=True)[0:listVal])/listVal
    # Grade A: 90-100 
    if average in range(90, 101):
        grade = 'A'
    # Grade B : 80-89
    elif average in range(80, 90):
        grade = 'B'
    # Grade C: 70-79
    elif average in range(70, 80):
        grade = 'C'
    # Grade D: 60-69
    elif average in range(60, 70):
        grade = 'D'
    # Grade Fail
    else:
        grade = 'F'

    return grade
```
