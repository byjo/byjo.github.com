## JVM(Java Virtual Machine)
: Write Once Run Anywhere를 가능하게 하기 위한 가상 머신
: 하나의 Java 실행파일(.class)이 os에 상관 없이 실행되게 하기 위해 생겨남

#### 특징
- 스택 기반
- 메모리 주소 기반의 레퍼런스 x, 심볼릭 레퍼런스 
- 가비지 컬렉션 : 클래스 인스턴스는 사용자 코드에 의해 명시적으로 생성되고, 가비지 컬렉션에 의해 자동으로 파기 
- 독립성 : 원시 타입(primitive type)을 정의하여 호환성, 독립성 보장
(c같은 경우에 long 타입의 크기가 os의 bit에 따라 32bit, 64bit로 변화)
cf. primitive type int는 reference type(class type) Integer에 의해 wrap되어 있음

#### Data Area
- Method
    + 정적인 데이터(바이트 코드, static)
    + os stack frame에서 text+data영역이라고 생각하면 됨 
- Heap
    + 동적 할당 된 데이터 
    + 생성된 인스턴스 저장 (new를 할 때 heap 영역에 메모리 할당)
    + reference type
    + 가비지 컬렉션 발생 (참조에 의한) -> null을 통해 메모리 누수 방지 
- Stack
    + frame(스레드 수행정보) 저장 
    + 지역변수, 매개변수, 임시 데이터 저장 
- Native
    + c코드와 같은 애들이 있음
- pc
    + 현재 수행중인 jvm 명령 주소 저장  




