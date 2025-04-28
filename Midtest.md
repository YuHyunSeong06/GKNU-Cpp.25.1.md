# 1
```cpp
#include <iostream>
#include <string>

class Person {
	std::string name;
	int age;
public:
	Person(std::string Na, int Ag) : name(Na), age(Ag) {}
	void displayInfo() { std::cout << name << ' ' << age << std::endl; }
};

int main()
{
	Person p("None", 20);
	p.displayInfo();
	return 0;
}
```

# 2
```cpp
#include <iostream>

int add(int a, int b)
{
	return a + b;
}

double add(double a, double b)
{
	return a + b;
}

int main()
{
	std::cout << add(1, 2) << std::endl;
	std::cout << add(1.1, 2.2);
	return 0;
}
```

# 3
```cpp
#include <iostream>
class Shape {
protected:
	int w, h;
public:
	Shape(int W, int H) : w(W), h(H) {}
	virtual int Area() = 0;
};

class Circle : public Shape {
public:
	Circle(int r) : Shape(r, r) {}
	int Area() { return w * h * 3.14; }
};

class Rectangle : public Shape {
public:
	using Shape::Shape;
	int Area() { return w * h; }
};

int main()
{
	Shape* p = new Circle(2);
	std::cout << p->Area() << std::endl;
	delete p;
	p = new Rectangle(2, 3);
	std::cout << p->Area() << std::endl;
	delete p;
	return 0;
}
```

# 4
```cpp
#include <iostream>
#include <string>

template<typename T>
void swapValues(T& a, T& b)
{
	T t = a;
	a = b;
	b = a;
	return;
}

int main()
{
	int a = 10, b = 20;
	std::cout << a << ' ' << b << std::endl;
	swapValues(a, b);
	std::cout << a << ' ' << b << std::endl;
	std::string s1 = "Hello ", s2 = "World ";
	std::cout << s1 << s2;
	swapValues(s1, s2);
	std::cout << s1 << s2;
	return 0;
}
```

# 5
#include <iostream>
#include <fstream>

int main() {
	try
	{
		std::ifstream ifs("input.txt");
		if (!ifs)
			throw "파일을 열 수 없습니다.";
		int a, b;
		ifs >> a >> b;
		std::cout << a << ' ' << b;
		ifs.close();
	}
	catch (const char* msg)
	{
		std::cerr << msg;
	}
	return 0;
}

# 6
```cpp
#include <iostream>
#include <vector>
#include <memory>

int main()
{
	std::vector<std::unique_ptr<int>> v;
	for (int i = 1; i < 10; i++)
		v.push_back(std::make_unique<int>(i));
	for (const auto& p : v)
	{
		if ([](const auto& ptr) {return *ptr % 2 == 0; }(p))
			std::cout << *p << ' ';
	}
	return 0;
}
```
