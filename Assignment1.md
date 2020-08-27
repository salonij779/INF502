## Assignment 1

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

    Initially, I get the length of the list by subtracting the number of elements to frop from the length of the original list. The next step is to calculate the average of the elements left in the list. To check what grade needs to be displayed I used if...elif...else to check for the grades and I have then displayed the grades.

The code is as follows:
```python
def grade_calc(grades_in, to_drop):
    listVal = len(grades_in) - int(to_drop)
    average = int(sum(sorted(grades_in, reverse=True)[0:listVal]) / listVal)
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


gradeList = [100, 95, 25, 78, 62, 45]
print(grade_calc(gradeList, 2))

gradeList = [89, 75, 35, 19, 46, 54]
print(grade_calc(gradeList, 3))

gradeList = [100, 95, 25, 78, 62, 45]
print(grade_calc(gradeList, 4))
```
The output for the code above is as follows:
```
B
C
A
```

4. Write a function with the following signature: odd_even_filter(numbers).

    To identify an element of the list to be even, I mod the element with 2 and if the remainder is 0, it is even and I append it to a list else it would be odd and I append that to another list.

The code is as follows:
```python
def odd_even_filter(numbers):
    even_list = []
    odd_list = []
    for x in range(0, len(numbers)):
        if numbers[x] % 2 == 0:
            even_list.append(numbers[x])
        else:
            odd_list.append(numbers[x])

    return even_list, odd_list


list1 = [1, 2, 3, 4, 5, 6, 7, 8, 9]
even1, odd1 = odd_even_filter(list1)
print('List1:' + str(list1))
print('Even:' + str(even1) + ' Odd:' + str(odd1))

list2 = [3, 9, 43, 7]
even2, odd2 = odd_even_filter(list2)
print('List2:' + str(list2))
print('Even:' + str(even2) + ' Odd:' + str(odd2))

list3 = [71, 39, 98, 79, 5, 89, 50, 90, 2, 56]
even3, odd3 = odd_even_filter(list3)
print('List3:' + str(list3))
print('Even:' + str(even3) + ' Odd:' + str(odd3))
```
The output for the above code is as follows:
```
List1:[1, 2, 3, 4, 5, 6, 7, 8, 9]
Even:[2, 4, 6, 8] Odd:[1, 3, 5, 7, 9]
List2:[3, 9, 43, 7]
Even:[] Odd:[3, 9, 43, 7]
List3:[71, 39, 98, 79, 5, 89, 50, 90, 2, 56]
Even:[98, 50, 90, 2, 56] Odd:[71, 39, 79, 5, 89]
```
