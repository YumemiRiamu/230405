# 230405

C++ 코딩 팀과제 

20191276 컴퓨터공학과 양용석 


## 1. 전위 ++ 연산자 오버로딩, 후위 ++ 연산자 오버로딩의 예시 를 만들고 설명

- 전위 ++ 연산자 오버로딩 예시

```
#include <iostream>
using namespace std;

class Number {
public:
    int value;
    
    Number(int v=0) : value(v) {}
    
    Number operator++() { // 전위 ++ 연산자 오버로딩
        ++value;
        return *this;
    }
};

int main() {
    Number n(1);
    ++n;
    cout << n.value << endl; // 출력값: 2
    return 0;
}
```
Number 클래스에 operator++ 함수를 정의하여 전위 ++ 연산자를 오버로딩합니다. </br>
operator++ 함수는 value 멤버 변수를 1 증가시킨 후, 객체 자신을 반환합니다.</br>
그리고 ++n을 호출하여 n 객체의 value 값을 1 증가시키고, 그 결과인 Number 객체를 다시 n에 저장합니다.</br>
마지막으로 n.value를 출력하여 결과값 2를 확인할 수 있습니다.


- 후위 ++ 연산자 오버로딩 에시

```
#include <iostream>
using namespace std;

class Number {
public:
    int value;
    
    Number(int v=0) : value(v) {}
    
    Number operator++(int) { // 후위 ++ 연산자 오버로딩
        Number temp(value);
        value++;
        return temp;
    }
};

int main() {
    Number n(1);
    n++;
    cout << n.value << endl; // 출력값: 2
    return 0;
}
```
 Number 클래스에 operator++ 함수를 정의하여 후위 ++ 연산자를 오버로딩합니다.</br>
 operator++ 함수는 value 멤버 변수를 먼저 임시 변수 temp에 저장한 후, value 값을 1 증가시킵니다. </br>
 그리고 임시 변수 temp를 반환합니다. 이때, 인자로 int 값을 받아야 하는데, 이는 후위 ++ 연산자가 구분되기 위한 구분자 역할을 합니다.</br>
 그리고 n++을 호출하여 n 객체의 value 값을 1 증가시키고, 증가 이전의 Number 객체를 반환합니다. 마지막으로 n.value를 출력하여 결과값 2를 확인할 수 있습니다.</br>



### 2. STL로 stack을 5개 만들고, 50, 40, 30, 20, 10을 저장하고, 출력 하는 것을 iterator를 활용한 코드 

아래가 작성한 코드입니다.</br>

```
#include <iostream>
#include <stack>
using namespace std;

int main() {
    // 5개의 스택 생성
    stack<int> s1, s2, s3, s4, s5;

    // 스택에 데이터 저장
    s1.push(50);
    s2.push(40);
    s3.push(30);
    s4.push(20);
    s5.push(10);

    // 스택 출력
    stack<int>::iterator it;
    for (it = s1.begin(); it != s1.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    for (it = s2.begin(); it != s2.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    for (it = s3.begin(); it != s3.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    for (it = s4.begin(); it != s4.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    for (it = s5.begin(); it != s5.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}
```

#### 3. ChatGPT를 활용하여 STL의 자료구조와 알고리즘을 분류하고, 자료구조 예제 1개와 알고리즘 1개를 만들기

 - 자료구조 : </br>

1. 시퀀스 컨테이너(Sequence Containers)</br>

  배열과 유사한 선형 자료구조</br>
  데이터의 삽입, 삭제, 검색, 정렬 등에 용이</br>
  벡터(vector), 리스트(list), 데크(deque) 등이 있음</br>
  
2. 연관 컨테이너(Associative Containers)</br>

  이진 탐색 트리 기반 자료구조</br>
  데이터의 삽입, 삭제, 검색, 정렬 등에 용이</br>
  맵(map), 멀티맵(multimap), 셋(set), 멀티셋(multiset) 등이 있음</br>

3. 컨테이너 어댑터(Container Adapters)</br>

  이미 존재하는 자료구조의 인터페이스를 변경하여 새로운 자료구조 형태로 사용 가능</br>
  스택(stack), 큐(queue), 우선순위 큐(priority_queue) 등이 있음</br>
  
-  자료구조 vector를 사용하여 정수 값을 저장하고 출력하는 코드</br>

```
#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4, 5};

    for (auto it = v.begin(); it != v.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}
```
  
- 알고리즘 : </br>

1. 비교자(Comparators)</br>

  두 값의 대소를 비교하는 함수를 제공</br>
  less, greater 등이 있음</br>

2. 검색(Searching)</br>

데이터를 검색하여 해당 값의 반복자를 반환하는 함수를 제공</br>
find, binary_search, lower_bound, upper_bound, equal_range 등이 있음</br>

3. 정렬(Sorting)</br>

데이터를 정렬하는 함수를 제공</br>
sort, stable_sort, partial_sort, nth_element 등이 있음</br>

4. 변형(Transformations)</br>

컨테이너에 저장된 값을 변환하여 새로운 컨테이너에 저장하는 함수를 제공</br>
copy, swap, fill, generate, remove, unique 등이 있음</br>

5. 수치 계산(Numeric Algorithms)</br>

컨테이너에 저장된 값을 이용하여 수치 계산을 수행하는 함수를 제공</br>
accumulate, inner_product, partial_sum, adjacent_difference 등이 있음</br>

6. 집합(Set Algorithms)</br>

집합 연산을 수행하는 함수를 제공</br>
merge, includes, set_union, set_intersection, set_difference, set_symmetric_difference 등이 있음</br>

- sort() 알고리즘을 사용하여 정수 값을 정렬하는 코드</br>

```
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main() {
    vector<int> v = {3, 1, 4, 2, 5};

    sort(v.begin(), v.end());

    for (auto it = v.begin(); it != v.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}

```

##### 4. C++의 주요 특징 20가지의 제목

1. 정적 타입 지원
2. 객체 지향 프로그래밍 (OOP) 지원
3. 다중 상속 지원
4. STL (Standard Template Library) 라이브러리 제공
5. 템플릿 지원
6. RAII (Resource Acquisition Is Initialization) 패턴 사용
7. 예외 처리 기능 제공
8. 포인터 지원
9. 함수 오버로딩 지원
10. 참조자 (Reference) 지원
11. 연산자 오버로딩 지원
12. 가상 함수 (Virtual Function) 지원
13. 함수 객체 (Functor) 지원
14. 스마트 포인터 (Smart Pointer) 제공
15. 예비 연산자 (Operator Ternary) 제공
16. 내장된 문자열 (String) 지원
17. 다양한 데이터 타입 지원
18. 네임스페이스 (Namespace) 지원
19. 표준 입출력 라이브러리 (iostream) 제공
20. 표준 라이브러리 (Standard Library) 포함.

###### 이상입니다 . 감사합니다.
