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
