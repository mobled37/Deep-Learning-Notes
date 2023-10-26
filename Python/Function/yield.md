reference: https://j-sik.tistory.com/126
```python
def yield_test(): 
	for i in range(5): 
		yield i 
		print(i,'번째 호출!') 
		
print(type(yield_test())) # <class 'generator'> 

#CaseA. __next__() 함수를 통해 출력 
t = yield_test() 
print(t.__next__()) # 0 
print(t.__next__()) # 0 번째 호출! 1 
print(t.__next__()) # 1 번째 호출! 2 
print(t.__next__()) # 2 번째 호출! 3 
print(t.__next__()) # 3 번째 호출! 4 

#print(t.__next__()) #Error 

#for문을 이용하여 출력 
print("<-->") 
for k in yield_test(): 
	print(k) 
	
#CaseB. result 
# 0 
# 0 번째 호출! 
# 1 
# 1 번째 호출! 
# 2 
# 2 번째 호출! 
# 3 
# 3 번째 호출! 
# 4 
# 4 번째 호출!
```

yield의 핵심은 **함수가 끝나지 않은 상태로 대기하고 있다는 것**이다. 필요할 때 마다 해당 객체를 통해 요소를 반환할 수 있기때문에 전체를 메모리에 저장할 필요가 없다는 점에서 굉장히 효율적이다. 