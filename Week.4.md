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

```cpp
// STL

#include <iostream>
#include < vector> // 배열 근데 이제 함수를 곁들인
                    // 배열 class
int main()
{
    std::vector<int> v = { 1,2,3, }; // v 라는 배열에 각 값들이 들어가있음
                                      // 배열과는 달리 크기에 제한이 없음
    int sum = 0;
    for (int x : v)
        sum += x;
    std::cout << sum << '\n';
    return 0;
}
```
