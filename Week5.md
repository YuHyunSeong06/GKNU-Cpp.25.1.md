```cpp
//// 템플릿
#include <iostream>
 
template <typename T>
 T Add(T a, T b) {
   return a + b;
}
int main()
{
    std::cout << Add(2, 3) << '\n';
    std::cout << Add(2.2, 3.3) << '\n';
}
```

```cpp
// STL
#include <iostream>
#include < vector>

int main()
{
    std::vector<int> v = { 1,2,3, };

    int sum = 0;

    for (int x : v)
        sum += x;

    std::cout << sum << '\n';

    return 0;
}
```

```cpp
#include <iostream>

class CPoly {
protected:
	int w, h;
public:
	CPoly(int a, int b) :w(a), h(b) {}
	virtual void Out() = 0;
};

class CRect : public CPoly {
public:
	CRect(int a=0, int b=0) :CPoly(a, b) {}
	void Out()  override{ std::cout << w << ", " << h << '\n'; }
};
int main()
{
	CRect r = CRect(2, 3);
	CPoly* p = &r;
	p->Out();
}
```
```cpp
#include <iostream>

template <typename T> 
T Add(T a, T b) {
    return a + b;
}

int main()
{
    std::cout << Add(2, 3) << '\n';
    std::cout << Add(2.2, 3.3) << '\n';
}
```

```cpp
#include <iostream>
#include < vector>

int main()
{
	std::vector<int>v = { 1,2,3, };

	int sum = 0;
	for (int x : v)
		sum += x;
	std::cout << sum << '\n';
	return 0;
}
```

```cpp
#include <iostream>

class CPoly {
protected:
	int w, h;
public:
	CPoly(int w, int h) { this->w = w; this->h = h; }
	virtual void Area() = 0;
};
class CRect : public CPoly {
public:
	using CPoly::CPoly; // using 사용한 부모 생성자의 상속
	void Area() override { std::cout << this->w * this->h << '\n'; }
};
int main()
{
	CRect r(2, 3);
	CPoly* p;
	p = &r;
	p->Area();//6
}
```

```cpp
#include <iostream>

class CPoly {
protected:
	int w, h;
public:
	CPoly(int _w, int _h) { w = _w; h = _h; }
	virtual void Area() = 0;
};
class CRect :public CPoly {
public:
	using CPoly::CPoly;
	void Area() override { std::cout << w * h << '\n'; }
};
class CTri :public CPoly {
public:
	using CPoly::CPoly;
	void Area() override { std::cout << w * h /2 << '\n'; }
};
int main()
{
	CPoly* p;
	CPoly* r = new CRect(2, 3);
	CTri* t = new CTri(2, 3);
	p = r;	p->Area();
	p = t;	p->Area();
	delete (r);
	delete (t);
}
```

```cpp
#include <iostream>
void inc(int& num) {
	num = num + 1;
}
int main() {
	int a = 0;
	inc(a);
	inc(a);
	inc(a);
	std::cout << a << '\n';
	return 0;
}
```

```cpp
#include <iostream>

template <typename T>
void sw(T& a, T& b) {
	T temp a;
	a = b;
	b = temp;
}

template <typename T>
void Pr(T& a,T& b) {
	std::cout << a << "," << b << '\n';
}
int main() {
	int x = 10, y = 20;
	sw<int>(x, y);
	std::cout << x << "," << y << '\n';
	double a = 1.5, b = 3.5;
	std::cout << a << "," << b << '\n';
}
```
