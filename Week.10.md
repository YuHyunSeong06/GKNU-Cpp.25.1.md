# 종합예제
```cpp
#include <iostream>
#include <vector>
#include <list>
#include <map>
#include <_________>  // sort, find, for_each 등
using namespace std;

// 출력용 함수 (for_each 알고리즘에서 사용)
void printInt(int n) {
    cout << n << " ";
}

int main() {
    // 1. 벡터 예제
    ______<int> vec = { 5, 2, 9, 1, 3 };
    
    // 벡터 출력 (이터레이터 사용)
    cout << "정렬 전 벡터: ";
    for(auto it = vec._____(); it != vec._____(); ++_____) {
        cout << ______ << " ";
    }
    cout << endl;
    
    // sort 알고리즘을 사용하여 벡터 정렬
    sort(vec._____(), vec._____());
    
    cout << "정렬 후 벡터: ";
    // for_each 알고리즘과 람다 함수를 사용하여 출력
    for_each(______.begin(), ______.end(), ___________(int n) { cout << n << " "; });
    cout << endl;
    
    // 2. 리스트 예제
    _______<string> strList = { "apple", "orange", "banana" };
    
    // 리스트 출력 (range-based for 문)
    cout << "리스트 내용: ";
    for (const _______ &s : _________) {
        cout << s << " ";
    }
    cout << endl;
    
    // 3. 맵 예제
    ______<______, _____> fruitCount;
    fruitCount["apple"] = 3;
    fruitCount["orange"] = 5;
    fruitCount["banana"] = 2;
    
    // 맵 출력 (이터레이터 사용)
    cout << "맵 내용:" << endl;
    for (auto it = fruitCount._____(); it != fruitCount.______(); ++it) {
        cout << it_____first << " : " << it_____second << endl;
    }
    
    return 0;
}
```
