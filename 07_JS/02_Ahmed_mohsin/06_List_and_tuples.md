```python
# list_one = [1,2,3,'d','t']  ordered set of element(any data type)/char(strin)
# list_two = [1,2,3,["Gangster"],'d','t']
# list_three = list((1,2,3,'d','t'))
# print(list_one[-1])
# print(list_one[1])
# print(list_one[0::2])
# print(list_one[-4:-1:2])
# # list digit is included
#
# # print(list_two)
# # print(list_three)
 
 
a = ['a','b','c',0,1,2,3,3]
a[0] = 'b'
 
print(a)
 
 
 
# b = ['a','b','c']
#
# # b = [4,5,6,'d','e','f']
 
# a.extend('x')
# # # print(a)
# # # print(a.append('x'))
# # print(a)
# a.pop()
# print(a)
# print(a)
# a.remove([1,2])
# print(a)
# print(a.count('a'))
# print(a)
# a.sort(reverse=True)
# print(a)
# b.sort(reverse=True)
# print(b)
# a.reverse()
# print(a)
 
# print(min(a))
# print(max(a))
# print(sum(a))

# Mutable
a = ['a','b','c',0,1,2,3,3]
print(a)
a[0] = 'b'
print(a)
# Immutable
# tuple_b = 1,2,3,'g','f'
tuple_c = (2,6,9,'A')
tuple_d = (4,9,2,'B')
tuple_f = (8,0,1,'C')
# tuple_c[0] = 'b'
print(tuple_c)
tuple_c = tuple_c[0],tuple_c[2],'S',tuple_f[2]
print(tuple_c)
 
ele_a,ele_b,ele_c,ele_d = tuple_c
 
print(ele_a)
print(ele_b)
print(ele_c)
print(ele_d)

# Range: To Create Automatic Lists
#
# my_list = [1,2,3,4,5,6,7,8,9]
# odd = [1,3,5,7,9]
# even = [2,4,6,8,10]
# print(my_list)
# print(odd)
# print(even)
#
# print(list(range(1,1000)))
# even = list(range(0,1000,2))
# odd = list(range(1,1000,2))
# print(even)
# print(odd)
# print(even[334])
# print(odd[420])
#
# print(odd.index(841))
 
 
# print(list(range(1,10)))
# even = list(range(0,10,2))
# odd = list(range(1,10,2))
# print(even)
# print(odd)
 
 
 
list_seven = range(17,100000,17)
num = int(input('Please enter your number:'))
print(f'{num} does exit in list:{num in list_seven}')
```
