**# vector**
```cpp
#include <iostream> 
#include <vector> // vector로 임의 접근
#include <algorithm> // 각종 알고리즘을 포함한다.

using namespace std; // vector, sort, cout

	int main() {
		vector <int> v = { 2,1,5,4,3 };
		sort(v.begin(), v.end()); // sort(start_iterator, end_iterator, compare); 매개변수
		for (auto i : v){    // 범위기반 for 문
			cout << i << ' ';
			cout << '\n';
		}
		for (int i = 0; i < v.size(); i++) { // 기본 for 문문
			cout << v[i] << ' ';
			cout << '\n';
		}
		return 0;
	}
 ```
**# list**
```cpp
#include <iostream> 
#include <list> // list로 요소 추가를 용이하게 한다.

using namespace std; // vector, sort, cout

int main() {
	list <string> li = { "apple", "orange", "banana" }; // list는 인덱스 접근이 불가능하다.
	for (auto& i : li) {
		cout << i << ' ';
		cout << endl;
	}
	return 0;
}
```
**# map**
```cpp
#include <iostream> 
#include <map> // 키로 값을 찾는다.

using namespace std; // vector, sort, cout

int main() {
	map <string, int> fc;
	fc["apple"] = 3;
	fc["orange"] = 5;
	fc["banana"] = 2;
	for (auto& i : fc) {
		cout << i.first << ' ' << i.second << endl;
		cout << endl;
	}
	return 0;
}
```
**# map**
```cpp
#include <iostream> 
#include <string>
#include <map> // 키로 값을 찾는다.

using namespace std; // vector, sort, cout

int main() {
	map <string, int> fc;
	fc["apple"] = 3;
	fc["orange"] = 5;
	fc["banana"] = 2;
	for (auto it = fc.begin(); it != fc.end(); ++it) { // iterator 활용 for 문문
		cout << it->first << ' ' << it->second << endl;
		cout << endl;
	}
	return 0;
}
```
