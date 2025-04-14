```cpp
#include <iostream> // auto

int main()
{
    auto a = 1;
    auto f = 1.1;
    auto s = "shim";
    std::cout << a <<f <<s;
}
```

```cpp
#include <iostream> // ramda

int main(){
	auto fn = [](auto a, auto b) {return a + b; };
	std::cout << fn();
}
```

```cpp
#include <iostream> // smart pointer

using namespace std;
int main() {
	unique_ptr<int> p = make_unique <int>(22);
	std::cout << *p;
}
```

```cpp
#include <iostream> // ramda

int main(){
	auto a = 2, b = 3;
	auto fn = [a,b]() {return a + b; };
	std::cout << fn();
}
```

```cpp
#include <iostream>
#include <memory> // auto_ptr, unique_ptr, share_ptr을 사용하기 위한 헤더

int main() {
	std::unique_ptr <int> p = std::make_unique <int>(20);
	// 직역 시 유일 포인터: 타 포인터에 전달하면 해당 포인터는 주소값을 넘겨주고 소멸
	// 자동 data가 되어 메모리 누수 방지
	std::cout << *p; // 포인터이기 때문에 * 연산자로 접근, 구조체나 클래스의 경우 ->로 접근한다.
	// delete p; unique_ptr이기 때문에 사용안함. 함수가 종료 될때 자동 delete
	return 0;
}
```

```cpp
#include <iostream>
#include <memory>

class CPnt {
private:
    int x, y;
public:
    CPnt(int x, int y) :x(x), y(y) {}
    void pr() const {
        std::cout << x << ", " << y << '\n';
    };
};
int main() {
    std::unique_ptr <CPnt> p = std::make_unique <CPnt>( 2,3 );
    p->pr();
}
```

```cpp
#include <iostream>
#include <memory>

class CPnt {
private:
    int x, y;
public:
    CPnt(int x, int y) :x(x), y(y) {}
    void pr() const {
        std::cout << x << ", " << y << '\n';
    };
};
int main() {
    CPnt me[3] = { {1,1},{2,2},{3,3} };
    me[0].pr();
}
```
