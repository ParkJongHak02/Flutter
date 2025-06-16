# 🚀 ParkJongHak02 - Flutter

---

## 📅 3주차 - 클래스, 상속, 인터페이스, 열거형, 컬렉션, 콜백 실습

---

### 📝 클래스 기본 생성 및 필드 수정

```dart
class Person {
  String name = "";
  int age = 0;
  
  void addOneYear() {
    age++;
  }
}

void main()
{
  var na = Person();
  na.name = '정세일';
  na.age = 48;
  print([na.name, na.age]);
}
```
---
### 📝 생성자 활용 및 getter/setter
```
class Person {
  // 클래스 필드 이름 앞에 '_'를 붙이는 것은 다수의 언어에서 사용하는 스타일임.
  // 예) Java, C++, C#
  String _name;
  int _age;
  String _desc;
  
  Person(this._name, this._age, this._desc);
  
  void addOneYear() {
    _age++;
  }
  
  String get name => _name;
  int get age => _age;
  String get desc => '$_desc!!!';
  set desc(String v) => _desc = v;
}

void main()
{
  var na = Person('정세일', 48, '정세일은 정세팔이다.');
  //na.name = '정세일';
  //na.age = 48;
  print([na.name, na.age, na.desc]);
  
  //na.name = '정세팔';
  //na.age++;
  na.addOneYear();
  na.desc = '아니다. 정세구다';
  
  print([na.name, na.age, na.desc]);
  
}
```
---
### 📝 생성자에 optional parameter 사용
```
class Person {
  String? name;
  int? age;

  Person({this.name, this.age});
  
}
  
void main()
{
  var p = Person(); // name: null, age: null
  var p2 = Person(name: '정세팔'); // name: 정세팔, age: null
  var p3 = Person(age: 48); // nage : null, age: 48
  var p4 = Person(name: '정세팔', age: 48);
}

```
---
### 📝 getter/setter 활용: Rectangle 클래스
```
class Rectangle {
  // 사각형을 왼쪽, 상단, 너비 , 높이로 표현
  num left, top, width, height;
  
  Rectangle(this.left, this.top, this.width, this.height);
  
  // 오른쪽 , 하단은 필드를 생성하지 않고 get/set으로 계산하여 표현
  num get right => left + width;
  set right(num value) => left = value - width;
  num get bottom => top + height;
  set bottom(num value) => top = value - height;
}

void main() 
{
  var r1 = Rectangle(5, 10, 20, 25);
  print([r1.left, r1.top, r1.width, r1.height]);
  print([r1.width, r1.height]);
  
  // left, top, width, height <-> left, top, right, bottom
}

```
---
### 📝 상속과 오버라이딩
```
class Hero {
  String name = '영웅';
  
  void run() {
    print('뛴다');
  }
}

class SuperHero extends Hero {
  @override
  void run() {
    super.run();
    this.fly();
  }
  
  void fly() {
    print('난다!');
  }
}

void main()
{
  var hero = SuperHero();
  hero.run();
  //hero.fly();
  print(hero.name);
}
```
---
### 📝 인터페이스 구현 (implements)
```
abstract class Monster {
  void attack();
}

class Goblin implements Monster {
  @override
  void attack() {
    print('고블린 어택!');
  }
}

class Bat implements Monster {
  @override
  void attack() {
    print('할퀴기!');
  }
}

void main()
{
  Goblin g1 = Goblin();
  Bat b1 = Bat();
  g1.attack();
  b1.attack();
  
  // monsters의 타입은?
  List<Monster> monsters = [g1, b1];
  monsters.forEach((m) => m.attack());
}
```
---
### 📝 열거형(enum) 활용
```
enum Status { login, logout }

void main()
{
  var authStatus = Status.logout;
  print(authStatus);
  
  switch (authStatus) {
    case Status.login:
      print('로그인');
      break;
    case Status.logout:
      print('로그아웃');
      break;
  }
}
```
---
### 📝 리스트, 맵, 셋 활용
```
void main()
{
  var l1 = [1,2,3,4,5,6];
  var l2 = ['가', '나', '다', '라', '마', '바'];
  print(l1);
  print(l2);
  
  l1.add(7);
  print(l1);
  l1.remove(2);
  print(l1);
  
  // 나라의 수도를 표현할때
  var m1 = {'한국': '서울', '일본': '도쿄'};
  print(m1);
  print(m1['한국']);
  m1['중국'] = '북경';
  
  var s1 = {1,2,3,3,3,4,5};
  print(s1);
  s1.add(6);
  print(s1);
  s1.add(6);
  print(s1);
}
```
---
### 📝 콜백 활용 (함수 포인터)
```
void func_a()
{
  print('왼쪽!');
}

void func_b()
{
  print('오른쪽!');
}

void main()
{
  var fun = func_a;
  fun();
  
  fun = func_b;
  fun();
  
  var list = [1,2,3,4,5];
  list.forEach(print);
}
```
