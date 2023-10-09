Similar to list, but some points
- list -> [], tuple -> () 
- 리스트는 요솟값의 생성, 삭제, 수정이 가능하지만 튜플은 요솟값을 바꿀 수 없다. 
> Tuple은 item을 변경할 수 없기 때문에 sort, insert, pop과 같은 내장 함수가 없다. 

***
**Making Tuple**
```python
t1 = ()
t2 = (1,)
t3 = (1, 2, 3)
t4 = 1, 2, 3
t5 = ('a', 'b', ('ab', 'cd'))
```

**When Delete Tuple items**
```python
t1 = (1, 2, 'a', 'b')
del t1[0]
```
```
Traceback (most recent call last): 
File "<stdin>", line 1, in <module> 
TypeError: 'tuple' object doesn't support item deletion
```

**When Change Tuple Items**
```python
t1 = (1, 2, 'a', 'b')
t1[0] = 'c'
```
```
Traceback (most recent call last): 
File "<stdin>", line 1, in <module> 
TypeError: 'tuple' object does not support item assignment
```
***
### tuple operation

**indexing**
```python
t1 = (1, 2, 'a', 'b')
t1[0]
```
```
1
```

**slicing**
```python
t1 = (1, 2, 'a', 'b')
t1[1:]
```
```
(2, 'a', 'b')
```

**adding**
```python
t1 = (1, 2, 'a', 'b')
t2 = (3, 4)
t3 = t1 + t2
t3
```
```
(1, 2, 'a', 'b', 3, 4)
```

**multiple**
```python
t2 = (3, 4)
t3 = t2 * 3
t3
```
```
(3, 4, 3, 4, 3, 4)
```

**length**
```python
t1 = (1, 2, 'a', 'b')
len(t1)
```
```
4
```

