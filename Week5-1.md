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
