# iot_cpp_study

# 1일차

- printf, scanf -> cout::, cin::
- Function Overloading(함수 오버로딩 - 다중정의)
- Default Value(디폴트 값)
- inline(인라인 함수)
- namespace(이름 공간) 조금
 선언 부분에 있는 기호들은 그냥 말그대로 기호다
 [& xx=] 참조자 별명, 시간 복잡도를 줄이기 위해서 씀 가리키기만 하니까, 얘는 기호
 선언 부분 이후에 쓰이는건 그냥 이름 자체로 쓴다.
 [* xx=] 포인터 주소 가리키는 애로 만들어, 얘는 기호
 선언부 이후에 왼쪽에 있든 오른쪽에 있든 그건 연산자.
 [= *xx] 주소에 존재하는 값(데이터가 배정 되어있는 칸 그 자체)를 반환해 (역참조) 널포인터 역참조하면 머리 깨짐
 [= &xx] 주소를 반환해

# 2일차

- namespace(이름 공간) - using namespace std;
- 메모리 공간
    - 코드 세그먼트, 데이터 세그먼트
        - 동적 데이터
        - 힙
        - 정적 데이터
        - 코드 
- bool 타입
- signed, unsigned, 부호비트, 비트연산자 (<<, >>)
- Call by Value(변수), Call by Reference(참조자 - 변수의 별칭), 더블 포인터 연산

역시 포인터는 볼 때마다 햇갈린다. 더블 포인터에서 포인터 하나를 빼면 그 전 주소값이 나오나? 아찔하네 c++

# 3일차

- Part1
    - Call by Reference(참조자 - 변수의 별칭)
        - https://dayday-kim.tistory.com/5
    - new & delete <== malloc & free 대신
    - 동적 할당
    - C++에서 C 표준함수 호출하기

- Part2
    - 구조체 Struct, Class
    - enum(열거형)
    ```cpp
    enum
    {
        ID_LEN  = 20,
        MAX_SPD  = 200,
        FUEL_STEP  = 2,
        ACC_STEP  = 10,
        BRK_STEP  = 10
    };

    ```
    - Class(클래스)와 Object(객체)
    ```c
    class Myclass{
         // 외부의 접근을 불허한다. (95%)
        private:
            int private_val;
        // 외부 접근 가능
        public:
            int public_val;
        // 상속에서만 접근 가능
        protected:
            int protected_val;
        public: // 멤버 함수 밖에서 쓰려면 public 무조건 써줘야된다.
            // 멤버 변수 값 바꾸는 법
            void set(int an)
            {
                private_val = an;
            }
            void get()
            {
                cout << "public_val : "<< public_val << endl;
                cout << "private_val : "<< private_val << endl;
            }
        };
    ```
    - 객체지향 프로그래밍
    - Infomation Hiding (정보은닉)

# 4일차

- 클래스 
    - Infomation Hiding (정보은닉) 나머지
        - const
    - Encapsulation (캡슐화)
    - Constructor(생성자)와 Destructor(소멸자)
        - 동적 할당 해제
        ```cpp
         MyClass(char aId, int aAge, const char* aName) : id(aId), age(aAge)
        {
            int len = strlen(aName) + 1;
            // 동적 할당을 하고 해제를 해야하는데 안하고 해제해서 오류 뜸
            name = new char[len];
            strcpy(name, aName);
        }
        ~MyClass()
        {
            delete []name; // 클래스 안에서 이름 넣는다고 쓴 heap 영역 해제
            cout << "call destructor!" << endl;
        }
        ```

# 5일차

- 클래스와 배열, this 포인터
    - 객체 배열
    - 객체 포인터 배열
    - this 포인터
- Copy Constructor(복사생성자)
    - 디폴트 복사생성자
    - 깊은 복사, 얕은 복사
    - 복사 생성자의 호출 시점 (어려움 확실하게 알아야됌)
        - 기존 객체를 이용해서 새로운 객체 생성
        - 함수 호출(Call_by_Value)시 객체를 인자로 전달
        - 객체를 반환 (참조형 X)

# 6일차

- friend와 static 그리고 const
    - const(값 못바꾸게 고정시킨다.)
    - friend(정보 은닉을 해치니 안쓰는게 좋다.)
    - static(전역,지역 특징을 골고루 가짐)
    - mutable(const 무효화)
- Inheritance(상속)
    - 부모클래스, 자식클래스
    - 상속의 문법적 이해
    - Protected 선언 및 3가지 형태의 상속
    - 상속을 위한 조건 (백수는 사람이야 아니야 ㄹㅇㅋㅋ)

# 7일차

- 