- Process of finding an alternate location when a collision occurs
	1. [[#Seperate Chaining]]
	2. [[#Open Addressing]]

### Seperate Chaining
**Chaining with [[linked lists]]**
- [[linked lists]]를 이용하는 방식, 각 index에 데이터를 저장하는 [[linked lists]]에 대한 포인터를 가지는 방식이다. 
- 만일 동일 index로 인하여 충돌이 발생하면 그 index가 가리키고 있는 [[linked lists]]에 노드를 추가하여 값을 추가한다.
- 데이터를 추출하고자 할때는 key에 대한 index를 구한 후 index가 가리키고 있는 linked list를 선형 검색하여, 해당 key에 대한 데이터가 있는지 검색하여 리턴하면 된다. 
- Key를 삭제할 땐, key에 대한 index가 가리키고 있는 [[linked lists]]에서 그 노드를 삭제하면 된다. 
- Lookup is **O(n)** in the worst case

**Chaining with binary search trees**
### Open Addressing
**Open addressing with Linear Probing**
- Hash table array의 빈공간을 사용하는 방법으로, separate chaining 방식에 비해 메모리를 덜 사용한다. 
- **Linear Probing**: index에 대해서 [[collision]]이 발생했을 때, index 뒤에 있는 버킷 중에 빈 버킷을 찾아서 데이터를 넣는 방식. 
- open addressing의 단점은 삭제가 어렵다는 것인데, 삭제를 한 경우 [[collision]]에 의해서 뒤로 저장된 데이터는 검색이 안될 수 있다. 
- Chaining과는 다르게, entry의 전체 숫자는 array의 사이즈에 제한을 받는다. 

**Open addressing with double hashing**



**Reference**
- [네이버 블로그](https://m.blog.naver.com/weplayicecream/221467971945)
- [해쉬 테이블의 이해와 구현 (Hashtable)](https://bcho.tistory.com/1072)
- 

