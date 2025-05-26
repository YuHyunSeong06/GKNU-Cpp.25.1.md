### 함수의 포인터
```cpp
#include <iostream>

int add(int a, int b) {
	return a + b;
}

int main() {
	int (*plus)(int, int) = add;
	std::cout << plus(1, 1);
	return 0;
}
```
### 람다함수
```cpp
#include <iostream>

int main() {
	int a = 2;
	int b = 3;
	std::cout << ([](int a, int b) {return a + b; }(a, b));
}
```

### 람다함수의 활용
```cpp
#include <iostream>

int main() {
	auto add = []() {return 2 + 3; };
	std::cout << add();
}
```
### 람다함수의 응용
```cpp
#include <iostream>

int main() {
	int a = 2; int b = 3;
	std::cout << [a](int b) {return a + b; }(b);
	return 0;
}
```

### 클래스와 스마트포인터
```cpp
#include <iostream>

class CRect {
	int a, b;
public:
	CRect(int a = 2, int b = 3) :a(a), b(b) {}
	void Pr() { std::cout << a << ' ' << b << '\n'; }
};

int main() {
	std::unique_ptr<CRect> p = std::make_unique <CRect>();
	p->Pr();
	return 0;
}
```

### 사진에 있는 숫자를 openCV를 이용해 추측해보기
```cpp
#include <opencv2/opencv.hpp>
#include <opencv2/dnn.hpp>
#include <iostream>
using namespace cv;
using namespace dnn;
using namespace std;

int main() {
    // 모델 경로 및 이미지 경로 설정
    string modelPath = "D:/mnist-8.onnx";
    string imagePath = "D:/8.png";

    // ONNX 모델 로드
    Net net = readNetFromONNX(modelPath);

    // 이미지 로드 및 전처리
    Mat img = imread(imagePath, IMREAD_GRAYSCALE);
    if (img.empty()) {
        cerr << "이미지를 불러올 수 없습니다: " << imagePath << endl;
        return -1;
    }
    resize(img, img, Size(28, 28));
    img.convertTo(img, CV_32F, 1.0 / 255);
    Mat blob = blobFromImage(img);  // (1, 1, 28, 28)

    // 입력 및 추론
    net.setInput(blob);
    Mat output = net.forward();  // 출력: (1, 10)

    // 결과 분석
    Point classId;
    double confidence;
    minMaxLoc(output, 0, &confidence, 0, &classId);
    cout << "예측된 숫자: " << classId.x << " (신뢰도: " << confidence << ")" << endl;

    return 0;
}
```
