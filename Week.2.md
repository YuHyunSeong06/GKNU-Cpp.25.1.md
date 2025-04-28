```cpp
#include <iostream>

class CRect {
private:
	int wid, hig;
public:
	int Area() { return wid * hig;}
	CRect(int a, int b);
};
CRect::CRect(int a, int b) {
	wid = a;
	hig = b;
}

		int main() {
			CRect r(3, 4);
				std::cout << r.Area();
		}
```
```cpp
#include <iostream>
#include <string>

using namespace std;
int main() {
	string s = "World ";
	cout << s << endl;
	//문자열 연결
	string cs = "Hello, " + s + "GKNU!!";
	cout << cs;
	return 0;
}
```
```cpp
//직사각형의 면적 구하기 클래스

#include <iostream>

using namespace std;
class CMath {
    int w, h;
public:
    CMath(int a, int b) { w = a; h = b; }
    CMath(int a) { w = h = a; }
    int Mul() { return w * h; }
};

int main()
{
    CMath m(3, 4);
    CMath n(5);
    std::cout << m.Mul() << endl;
    std::cout << n.Mul();
}
```

```cpp

//직사각형의 면적 구하기 함수

#include <iostream>

int Area(int w, int h)
{
	return w * h;
}

int main()
{
	int wid = 3, hig = 4;
	std::cout << Area(wid, hig);
	return 0;
}
```

```cpp
//직사각형의 면적 구하기 구조체
#include <iostream>

struct CRect {
	int w; int h;
int mul(int w, int h) {
	return w * h;
};
int main()
{
struct CRect m ={3,4};]
cout << mul(m.w, m.h) << endl;
return 0;
}
```


