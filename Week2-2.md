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
