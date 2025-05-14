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
```cpp
#include <iostream>

class CPnt {
    int x, y;
public:
    CPnt(int _x = 2, int _y = 3) :x(_x), y(_y) {}
    void Output(void) { std::cout << x << ", " << y << '\n'; }
};
int main()
{
    CPnt* p= new CPnt (2,3);
    p->Output();
    delete p;

}
```
```cpp
#include <iostream>

class CPnt {
    int x, y;
public:
    CPnt(int _x = 2, int _y = 3) :x(_x), y(_y) {}
    void Output(void) { std::cout << x << ", " << y << '\n'; }
    const CPnt Add(const CPnt& p) {
        CPnt t;
        t.x = this->x + p.x;
        t.y = this->y + p.y;
        return t0;
    }
};
int main()
{
    CPnt p1(1, 1), p2(2, 2), p3;
    p3 = p1.Add(p2);
    p3.Output();
}
```

```cpp
#include <iostream>

using namespace std;
class CPnt {
	int x, y;
public:
	CPnt(int x = 0, int y = 0) :x(x), y(y) {}
	void OUt() { cout << x << ', ' << y << '\n'; }
};
int main() {
	// CPnt* p = new CPnt(1,1);
	unique_ptr<CPnt> p = make_unique<CPnt>(1,1);// 스마트 포인터
	p->OUt();
	// delete 불필요 : unique_ptr이 자동으로 메모리 해제
}
```

```cpp
#include <iostream>

using namespace std;
class CPnt {
	int x, y;
public:
	CPnt(int x = 0, int y = 0) :x(x), y(y) {}
	void OUt() { cout << x << ', ' << y << '\n'; }
};
int main() {
	try {
		CPnt* p = new CPnt();
		p->OUt();
		int c = 0;
		int a = 3 / c;
		delete p;
	}
	catch (...) {
		cout << "예외발생!\n";
	}
}
```
