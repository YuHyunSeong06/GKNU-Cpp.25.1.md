### ✅ C언어와 중복되지 않는 **C++ 전용 개념 15선**

1. **클래스와 객체 (OOP의 핵심)**
2. **생성자와 소멸자**
3. **접근 지정자 (`public`, `private`, `protected`)**
4. **상속 (`inheritance`)**
5. **다형성과 가상 함수 (`virtual`, `override`)**
6. **함수 오버로딩**
7. **연산자 오버로딩**
8. **템플릿 함수와 클래스 (`template`)**
9. **예외 처리 (`try`, `catch`, `throw`)**
10. **STL(Standard Template Library): vector, list, map, iterator 등**
11. **스마트 포인터 (`unique_ptr`, `shared_ptr` 등, C++11 이상)**
12. **람다 함수 (Lambda Expression)**
13. **`auto`, `decltype`, `constexpr` 등의 C++ 확장 키워드**
14. **네임스페이스 (`namespace`)와 C++ 코드 구조화**
15. **헤더와 소스 파일 분리 및 클래스 모듈화 방식**

# SQlite3를 이용한 코드
#### sqlite3 사이트에서 다운로드 후 압축을 풀고  
#### visual studio 2022에서 솔루션 탐색기를 통해 
#### 코드의 위치를 추적해 파일을 넣는다.
```cpp
#include <iostream>
#include "sqlite3.h"
#include <string>
using namespace std;

int main() {
    sqlite3* db;
    char* errMsg = nullptr;
    int rc;

    // 데이터베이스 연결
    rc = sqlite3_open("sample.db", &db);
    if (rc) {
        cerr << "데이터베이스 열기 실패: " << sqlite3_errmsg(db) << endl;
        sqlite3_close(db);
        return 1;
    }

    // 테이블 생성
    const char* createTableQuery =
        "CREATE TABLE IF NOT EXISTS Users ("
        "ID INTEGER PRIMARY KEY AUTOINCREMENT, "
        "Name TEXT, "
        "Age INTEGER);";

    rc = sqlite3_exec(db, createTableQuery, nullptr, nullptr, &errMsg);
    if (rc != SQLITE_OK) {
        cerr << "테이블 생성 실패: " << errMsg << endl;
        sqlite3_free(errMsg);
        sqlite3_close(db);
        return 1;
    }

    // 데이터 삽입
    const char* insertQuery =
        "INSERT INTO Users (Name, Age) VALUES "
        "('Alice', 30), "
        "('Bob', 25);";

    rc = sqlite3_exec(db, insertQuery, nullptr, nullptr, &errMsg);
    if (rc != SQLITE_OK) {
        cerr << "데이터 삽입 실패: " << errMsg << endl;
        sqlite3_free(errMsg);
        sqlite3_close(db);
        return 1;
    }

    // 데이터 조회
    const char* selectQuery = "SELECT * FROM Users;";
    sqlite3_stmt* stmt;

    rc = sqlite3_prepare_v2(db, selectQuery, -1, &stmt, nullptr);
    if (rc != SQLITE_OK) {
        cerr << "쿼리 준비 실패: " << sqlite3_errmsg(db) << endl;
        sqlite3_close(db);
        return 1;
    }

    cout << "Users 테이블 데이터:" << endl;
    while (sqlite3_step(stmt) == SQLITE_ROW) {
        int id = sqlite3_column_int(stmt, 0);
        const unsigned char* name = sqlite3_column_text(stmt, 1);
        int age = sqlite3_column_int(stmt, 2);

        cout << "ID: " << id
            << ", Name: " << (name ? reinterpret_cast<const char*>(name) : "NULL")
            << ", Age: " << age << endl;
    }

    // 리소스 해제
    sqlite3_finalize(stmt);
    sqlite3_close(db);

    return 0;
}
```
# OpenCV를 통한 코드
#### NuGet 패키지를 통해 OpenCV 4.2를 다운적용시킨다
### 사각형 그리기
```cpp
#include <opencv2/opencv.hpp>

int main() {
    // 1. 400x400 크기의 검은색 배경 이미지 생성
    cv::Mat image = cv::Mat::zeros(400, 400, CV_8UC3);

    // 2. 사각형의 시작점(왼쪽 위)과 끝점(오른쪽 아래)
    cv::Point pt1(100, 100);
    cv::Point pt2(300, 300);

    // 3. 색상 (B, G, R) - 파란색
    cv::Scalar color(0, 255, 0);

    // 4. 두께 (음수: 채우기, 양수: 테두리 두께)
    int thickness = -1;

    // 5. 사각형 그리기
    cv::rectangle(image, pt1, pt2, color, thickness);

    // 6. 결과 이미지 표시
    cv::imshow("Rectangle", image);
    cv::waitKey(0);
    return 0;
}
```
### 심재창 교수님 사진 출력
#### 사진도 소스파일에 추가한다
```cpp
#include <opencv2/opencv.hpp>
#include <iostream>

using namespace cv;
using namespace std;

int main() {
    // 1. 이미지 파일 읽기
    Mat img = imread("mosajb8iV4.jpg");  // sample.jpg 파일을 읽어옴 <- 반드시 확인하세요.
    if (img.empty()) {
        cerr << "이미지를 불러올 수 없습니다." << endl;
        return -1;
    }

    // 2. 그레이스케일 변환
    Mat gray;
    cvtColor(img, gray, COLOR_BGR2GRAY);

    // 3. 이미지 출력
    imshow("Original Image", img);  // 원본 이미지 출력
    imshow("Gray Image", gray);       // 그레이스케일 이미지 출력

    // 4. 키 입력 대기 (0이면 무한대기)
    waitKey(0);

    return 0;
}
```
