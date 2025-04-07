```cpp
#include <iostream>

using namespace std;
template <typename T>

T Add(T& a, T& b) {
    return a + b;
}
int Add(int a, int b) {
    return a + b;
}
double Add(double a, double b) {
    return a + b;
}

int main()
{
    int a1 = 2, b1 = 3;
    cout << Add(2, 3)<<'\n';
    cout << Add(2.2, 2.3) << '\n';
}
```

```cpp
#include <iostream>
template < typename T>
class CMy {
	T a, b;
public:
	CMy(T a, T b) {
		this->a = a; this->b = b;
	}
	void Add() { std::cout << a + b << '\n'; }
};
int main() {
	CMy<double>* p = new CMy<double>(2.2, 3.3); // heap
	p->Add();
	delete p;
}
```

```cpp
#include <iostream>
#include <vector>
int main() {
	std::vector <int> v = { 1,2,3,4 };
	v.push_back(5);
	int s = 0;
	for (int x : v)s += x;
	std::cout << s << '\n';

}
```
