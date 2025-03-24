```cpp
// 다각형으로 부터, 삼각형, 사각형 면적계산 : 상속
#include <iostream>

class P { // base 클래스
protected:
	int w, h;//
public:
	P(int x, int y) : w(x), h(y) {}
};
class T : public P { // drived 클래스
public:
	T(int x, int y) : P(x, y) {}
	void A() { std::cout << w * h / 2 << '\n'; }
};
class R : public P { // drived 클래스
public: R(int x, int y) :P(x, y) {}
	  void A() {
		  std::cout << w * h << '\n';
	  }
};
	
int main() 
{
	T t(1, 2); t.A(); // 삼각형의 너비와 높이
	R r(1, 2); r.A(); // 사각형의 너비와 높이
	return 0;
}
```
