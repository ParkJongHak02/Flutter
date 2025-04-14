# ParkJongHak02 - Flutter


## 6주차 과제<br/><페이지 203 ~ 208 페이지 내용 실습 및 요약>
위젯의 라이프사이클 확인
<br/>
<br/>
화면의 Stack구조 - push(), pop()시 호출되는 메소드 출력
- initState()
- ispose()
- build()

# 📘 Flutter 위젯 생명주기 실습 요약 (p.203 ~ p.208)


StatelessWidget과 StatefulWidget의 `build()`, `initState()`, `dispose()` 메서드의 호출 시점을 실습을 통해 확인

---

## 📌 실습 개요

- `StatelessWidget`과 `StatefulWidget`의 라이프사이클 이해
- 화면 간 전환 시 어떤 메서드가 호출되는지 로그로 확인
- `Navigator.push()` / `Navigator.pop()` 사용 흐름 분석

---

## 🧪 StatelessWidget 실습

### ✅ 핵심 내용
- `build()`는 화면이 표시될 때마다 호출된다.
- `push()` → 새로운 페이지의 `build()` 호출
- `pop()` → 이전 페이지의 `build()` 다시 호출
- `print()` 로그로 메서드 호출 확인

### 📄 예시 출력 로그
```bash
FirstPage build()
SecondPage build()
ok
```

---

## ✅ **2. 실습용 전체 코드 **  


---

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: FirstPage(),
  ));
}

// StatelessWidget 실습
class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    print('FirstPage build()');
    return Scaffold(
      appBar: AppBar(title: Text('FirstPage')),
      body: Center(
        child: ElevatedButton(
          child: Text('Go to SecondPage'),
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (_) => SecondPage()),
            ).then((value) {
              print(value); // 'ok' 출력
            });
          },
        ),
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    print('SecondPage build()');
    return Scaffold(
      appBar: AppBar(title: Text('SecondPage')),
      body: Center(
        child: ElevatedButton(
          child: Text('Go Back'),
          onPressed: () {
            Navigator.pop(context, 'ok');
          },
        ),
      ),
    );
  }
}

// StatefulWidget 실습
class Person {
  final String name;
  final int age;
  Person(this.name, this.age);
}

class FirstStatefulPage extends StatefulWidget {
  @override
  _FirstStatefulPageState createState() => _FirstStatefulPageState();
}

class _FirstStatefulPageState extends State<FirstStatefulPage> {
  @override
  void initState() {
    super.initState();
    print('FirstPage initState()');
  }

  @override
  void dispose() {
    print('FirstPage dispose()');
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    print('FirstPage build()');
    return Scaffold(
      appBar: AppBar(title: Text('First')),
      body: Center(
        child: ElevatedButton(
          child: Text('다음 페이지로'),
          onPressed: () {
            final person = Person('홍길동', 20);
            Navigator.push(
              context,
              MaterialPageRoute(
                builder: (_) => SecondStatefulPage(person: person),
              ),
            );
          },
        ),
      ),
    );
  }
}

class SecondStatefulPage extends StatefulWidget {
  final Person person;
  const SecondStatefulPage({Key? key, required this.person}) : super(key: key);

  @override
  _SecondStatefulPageState createState() => _SecondStatefulPageState();
}

class _SecondStatefulPageState extends State<SecondStatefulPage> {
  @override
  void initState() {
    super.initState();
    print('SecondPage initState()');
  }

  @override
  void dispose() {
    print('SecondPage dispose()');
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    print('SecondPage build()');
    return Scaffold(
      appBar: AppBar(title: Text(widget.person.name)),
      body: Center(
        child: ElevatedButton(
          child: Text('이전 페이지로'),
          onPressed: () {
            Navigator.pop(context);
          },
        ),
      ),
    );
  }
}

