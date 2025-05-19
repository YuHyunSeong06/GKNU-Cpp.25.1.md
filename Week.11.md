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
