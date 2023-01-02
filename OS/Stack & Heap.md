# Stack & Heap

![메모리 할당 영역](https://user-images.githubusercontent.com/105041834/210197033-346e91a3-fede-4491-8ac6-fb5879f825cd.jpg)

- code 영역
  - 프로그램의 코드가 저장되는 영역 (text)
  - CPU는 코드 영역에 저장된 명령어를 하나씩 가져가서 처리

- Data 영역 (Static Memory Allocation)
  - 전역변수와 정적(static)변수가 존재 (static int)
  - **프로그램의 시작과 함께 할당이 되고 프로그램이 종료되면 소멸한다.**
  - 초기화 되면 (data) 초기화 안되면 (bss) (옛날)

- Stack 영역 (Static Memory Allocation)
  - 함수의 호출과 그 내부 매개 변수들이 저장됨.
  - LIFO(Last In First Out)의 구조를 가진다.
  - 함수의 호출과 함께 할당됨, 함수의 호출이 완료되면 소멸한다.
  - ex) int main () {...}

- Heap 영역 (Dynamic Memory Allocation)
  - 사용자가 직접 관리하는 메모리 영역.

## Reference
- [Reference](https://junghyun100.github.io/%ED%9E%99-%EC%8A%A4%ED%83%9D%EC%B0%A8%EC%9D%B4%EC%A0%90/)