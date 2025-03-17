```cpp
// 상속
// inheritance
// protected
// class CRect : public
// 


#include <iostream>// 전처리 함수	

using namespace std;// 원래는 std cout << 이지만 이걸로 인해 std 생략 가능 또한 endl도 원래는 std endl임

class CPoly // CPoly라는 클래스 생성
{
protected:// private: 그안에서의 클래스에서만 사용가능 하지만 protected는 자기 자신과 상속된 이들까지 사용가능
	int w, h;// w, h 각각 너비와 높이 선언
public:// public: 모두 쓸수있음
	CPoly(int x, int y) : w(x), h(y) {}// 각각 x 와 y를 선언하고 w 와 h에 x, y를 대입
};

class CRect : public CPoly {// CRect에 CPoly를 상속받기 
public://마찬가지
	CRect(int x, int y) : CPoly(x, y) {}// 상속할대 int 뒤에 x 와 y 를 따로 대입할 필요없이 CPoly(x,y)로 대체
	int Area() {// Area: 멤버함수 구조체는 안에 내용밖에 못넣지만 Area는 함수까지 포함 가능
		return w * h;// return을 통해 w * h 값을 반환하기
	}
};
int main()// 메인함수
{
	CRect* p;// 포인터...? 일단 킵 아마도 포인터 변수 p 선언
	p = new CRect(3, 7);// 선언된 p 를 엄청 길었던거를 new로 퉁치기
	cout << p->Area()<< endl;// cout << p.Area였는데 포인터때문에 p->Area
	delete p;// 할당한 메모리를 해제
}
```
