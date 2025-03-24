```cpp
#include <iostream>

class CPnt {
	int x, y;
public:
	CPnt(){}// 기본 생성자 를 넣어주거나 a 와 b 에 초기값 대입
	CPnt(int a , int b) {
		x = a; y = b;
	}
	void Out() {
		std::cout << x << " " << y << "\n";}
	CPnt Add(CPnt& p) {
		return CPnt(x + p.x, y + p.y);
	}
	};
int main() {
	CPnt p1(1, 1), p2(2, 2), p3;
	p3 = p1.Add(p2);
	//p3 = p1 + p2;
	p3.Out();
}
```
