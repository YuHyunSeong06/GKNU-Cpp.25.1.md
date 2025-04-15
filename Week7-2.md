```cpp
#include <iostream>
#include <fstream>

int main() {
    std::ofstream("my.txt")<< 11 << ' ' << 22;

    return 0;
}
```

```cpp
#include <iostream>
#include <fstream> // file stream 의 약자

int main()
{
    int a, b;
    std::ifstream of("my.txt"); of >> a >> b;
    std::cout << a + b;
}
```

```cpp
#include <iostream>
#include <fstream>

int main() 
{
    int a = 10, b = 0;
    try {
        if (b == 0) {
            throw 88.11;
        
        }
        std::cout << "결과: " << (a / b) << std::endl;
    }
    catch (...) // ...을 통해 char, int ,double 모두 될 수 있다
    {
        std::cout << "예외 발생:" << a << std::endl;
    }
}
```

```cpp
#include <iostream>
#include <fstream>

int main()
{
    int a = 2, b ;
    std::cout << "숫자입력:";
    std::cin >> b;
    try {
        if (b == 0) {
            throw "Div by 0";
        }
        std::cout << a / b;

        }
    catch (const char* p) {
        std::cerr << p;
    }
    return 0;
}
```

```cpp
#include <iostream>
#include <memory> // 스마트 포인터 사용을 위한 헤더

using namespace std;

// CPnt 클래스 정의
class CPnt {
private:
    int x, y; // 점의 좌표

public:
    CPnt(int x, int y) : x(x), y(y) {}
    void pr() const { cout << "(" << x << ", " << y << ")" << endl; }
};

int main() {
    unique_ptr<CPnt> pnt[3]; // 스마트 포인터 배열

    pnt[0] = make_unique<CPnt>(1, 1);
    pnt[1] = make_unique<CPnt>(2, 2);

    for (auto& a : pnt) {
        a->pr();
    }

    return 0;
}
```
