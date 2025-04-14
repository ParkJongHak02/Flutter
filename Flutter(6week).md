# ParkJongHak02 - Flutter


## 6주차


### 수업 정리
```
import 'package:a_6_1/second_page.dart';
import 'package:flutter/material.dart';
import 'package:a_6_1/Person.dart';

class FirstPage extends StatelessWidget {
  const FirstPage({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('FirstPage')),
      body: Text('!!!'),
      floatingActionButton: ElevatedButton(
        onPressed:
            () async {
              final person = Person('홍길동', 20);

          // var result = await Navigator.push(
          //   context,
          //   MaterialPageRoute(builder: (context) => SecondPage(person: person)),
          // );
          var result = await Navigator.pushNamed(context, '/second', arguments: person);

          print(result);
        },
        child: Text('다음 페이지로'),
      ),
    );
  }
}
```

```
import 'package:flutter/material.dart';
import 'package:a_6_1/Person.dart';

class SecondPage extends StatelessWidget {
  final Person? person;

  const SecondPage({super.key, this.person});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('SecondPage')),
      body: Text('${person?.name}, ${person?.age}'),
      floatingActionButton: ElevatedButton(
          onPressed: () {
            Navigator.pop(context, "동작했음!");
          },
      child: Text('이전 페이지로'),
      ),
    );
  }
}

```

```
import 'package:flutter/material.dart';
import 'package:a_6_1/first_page.dart';
import 'package:a_6_1/second_page.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(

        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
      ),
      home: const FirstPage(),
      routes: {
        '/first': (context) => FirstPage(),
        '/second': (context) => SecondPage(),
      }
    );
  }
}
```

```
class Person {
  String name;
  int age;

  Person(this.name, this.age);
}
```
### 화면 출력
![1 (1)](https://github.com/user-attachments/assets/a33be731-9e8f-4569-b923-da00a7804483)
![2 (1)](https://github.com/user-attachments/assets/5ae20298-cf5b-49c3-a42b-f40eb49d14f8)
![3 (1)](https://github.com/user-attachments/assets/61d6e121-0b3c-46b1-b62c-480bb330ee88)
![4 (1)](https://github.com/user-attachments/assets/7545d57d-0ab8-4fde-bc63-836d5672d8e9)
![5 (1)](https://github.com/user-attachments/assets/9c008b5f-e9e9-419e-8892-8c0ee7333ec0)
