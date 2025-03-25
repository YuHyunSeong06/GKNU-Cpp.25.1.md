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
