# 🚀 ParkJongHak02 - Flutter

---

## 📅 6주차 - Flutter 페이지 이동, 입력 위젯 및 다이얼로그 실습

---

## 📝 실습 1 (a_6_1) - Navigator, Route, 데이터 전달


---
### 📄first_page.dart
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
  
---
### 📄second_page.dart
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
  
---
### 📄main.dart
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
  
---
### 📄Person.dart
  ```
  class Person {
    String name;
    int age;
  
    Person(this.name, this.age);
  }
  ```
---
### 📝 실습 2 (a_6_3) - 다양한 입력 위젯 및 이벤트 처리
  
---
### 📄main.dart
  ```
  import 'package:a_6_3/test_DropDownButton.dart';
  import 'package:a_6_3/test_Gesture.dart';
  import 'package:a_6_3/test_TextField.dart';
  import 'package:a_6_3/test_dialog.dart';
  import 'package:flutter/material.dart';
  import 'package:a_6_3/test_CheckBox.dart';
  import 'package:a_6_3/test_Radio.dart';
  
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
        // home: const MyHomePage(title: 'Flutter Demo Home Page'),
      //  home: TestTextField(),
        //  home: TestCheckbox(),
        //home: TestRadio(),
        // home: TestDropdownbutton(),
        // home: TestDialog(),
        home: TestGesture(),
      );
    }
  }
  
  // class MyHomePage extends StatefulWidget {
  //   const MyHomePage({super.key, required this.title});
  //
  //
  //
  //   final String title;
  //
  //   @override
  //   State<MyHomePage> createState() => _MyHomePageState();
  // }
  //
  // class _MyHomePageState extends State<MyHomePage> {
  //   int _counter = 0;
  //
  //   void _incrementCounter() {
  //     setState(() {
  //
  //       _counter++;
  //     });
  //   }
  //
  //   @override
  //   Widget build(BuildContext context) {
  //
  //     return Scaffold(
  //       appBar: AppBar(
  //
  //         backgroundColor: Theme.of(context).colorScheme.inversePrimary,
  //
  //         title: Text(widget.title),
  //       ),
  //       body: Center(
  //         // Center is a layout widget. It takes a single child and positions it
  //         // in the middle of the parent.
  //         child: Column(
  //
  //           mainAxisAlignment: MainAxisAlignment.center,
  //           children: <Widget>[
  //             const Text('You have pushed the button this many times:'),
  //             Text(
  //               '$_counter',
  //               style: Theme.of(context).textTheme.headlineMedium,
  //             ),
  //           ],
  //         ),
  //       ),
  //       floatingActionButton: FloatingActionButton(
  //         onPressed: _incrementCounter,
  //         tooltip: 'Increment',
  //         child: const Icon(Icons.add),
  //       ), // This trailing comma makes auto-formatting nicer for build methods.
  //     );
  //   }
  // }
  
  ```
  
---
### 📄test_CheckBox.dart
  ```
  import 'package:flutter/material.dart';
  
  class TestCheckbox extends StatefulWidget {
    const TestCheckbox({super.key});
  
  
    @override
    State<TestCheckbox> createState() => _CheckboxState();
  }
  
  class _CheckboxState extends State<TestCheckbox> {
   bool? isChecked1 = false;
   bool isChecked2 = false;
  
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          backgroundColor: Theme.of(context).colorScheme.inversePrimary,
          title: Text('Checkbox / Switch 테스트'),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Checkbox(
                  value: isChecked1,
                  onChanged: (value) {
                    setState(() {
                      isChecked1 = value;
                    });
                  }
              ),
  
              SizedBox(height: 80),
  
              Switch(
                  value: isChecked2,
                  onChanged: (value) {
                    setState(() {
                      isChecked2 = value;
                    });
                  },
               ),
             ],
            ),
          ),
        );
      }
    }
  
  ```
  
---
### 📄test_dialog.dart
  ```
  import 'package:flutter/material.dart';
  
  class TestDialog extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(title: Text('다이얼로그 테스트')),
        body: Padding(
          padding: EdgeInsets.all(16.0),
          child: Column(
            children: [
              ElevatedButton(
                onPressed: () {
                  showDialog(
                    context: context,
                    barrierDismissible: false,
                    builder: (BuildContext context) {
                      return AlertDialog(
                        title: Text('제목'),
                        content: SingleChildScrollView(
                          child: ListBody(
                            children: [
                              Text('Alert Dialog입니다.'),
                              Text('OK를 눌러 닫습니다.'),
                            ],
                          ),
                        ),
                        actions: [
                          TextButton(
                            child: Text('OK'),
                            onPressed: () {
                              Navigator.of(context).pop();
                            },
                          ),
                          TextButton(
                            child: Text('Cancel'),
                            onPressed: () {
                              Navigator.of(context).pop(false);
                            },
                          ),
                        ],
                      );
                    }, // ← 이 괄호 다음에 세미콜론 빠뜨리면 오류남!
                  );
                },
                child: Text('Alert Dialog'),
              ),
            ],
          ),
        ),
      );
    }
  }
  
  ```
  
---
### 📄test_DropDownButton.dart
  ```
  import 'package:flutter/material.dart';
  
  class TestDropdownbutton extends StatefulWidget {
    const TestDropdownbutton({super.key});
  
    @override
    State<TestDropdownbutton> createState() => _DropDownButtonState();
  }
  
  class _DropDownButtonState extends State<TestDropdownbutton> {
    final _valueList = ['첫번째', '두번째', '세번째'];
    String? _selectedValue = '첫번째';
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          backgroundColor: Theme.of(context).colorScheme.inversePrimary,
          title: Text('DropDownButton 테스트'),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              DropdownButton<String>(
                value: _selectedValue,
                items: _valueList
                    .map((value) => DropdownMenuItem(
                  value: value,
                  child: Text(value),
                ))
                    .toList(),
                onChanged: (value) {
                  setState(() {
                    _selectedValue = value;
                  });
                  print(_selectedValue);
                },
              ),
            ],
          ),
        ),
      );
    }
  }
  
  ```
  
---
### 📄test_Gessture.dart
  ```
  import 'package:flutter/material.dart';
  
  class TestGesture extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(title: Text(' GestureDetctor, InkWell 테스트')),
        body: Padding(
          padding: EdgeInsets.all(16.0),
          child: Column(
            children: [
              GestureDetector(
                onTap: () {
                  print: Text('GestureDetctor!!');
              },
                child: Text('클릭돼'),
              ),
              
              SizedBox(height: 80),
              
              InkWell(
                onTap: () {
                  print: Text('Inkwell!!');
                },
                child: Text('클릭돼?'),
              ),
            ],
          ),
        ),
      );
    }
  }
  
  ```
  
---
### 📄test_Radio.dart
  ```
  import 'package:flutter/material.dart';
  
  enum Gender {
    MAN,
    WOMAN,
  }
  
  class TestRadio extends StatefulWidget {
    const TestRadio({super.key});
  
    @override
    State<TestRadio> createState() => _RadioState();
  }
  
  class _RadioState extends State<TestRadio> {
    Gender? _gender = Gender.MAN;
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          backgroundColor: Theme.of(context).colorScheme.inversePrimary,
          title: Text('Checkbox / Switch 테스트'),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              ListTile(
                title: Text('남자'),
                leading: Radio(
                  value: Gender.MAN,
                  groupValue: _gender,
                  onChanged: (value) {
                    setState(() {
                      _gender = value;
                    });
                  },
                ),
              ),
              ListTile(
                title: Text('여자'),
                leading: Radio(
                  value: Gender.WOMAN,
                  groupValue: _gender,
                  onChanged: (value) {
                    setState(() {
                      _gender = value;
                    });
                  },
                ),
              ),
              SizedBox(height: 80),
  
              RadioListTile<Gender>(
                title: Text('남자'),
                value: Gender.MAN,
                groupValue: _gender,
                onChanged: (value) {
                  setState(() {
                    _gender = value;
                  });
                },
              ),
              RadioListTile<Gender>(
                title: Text('여자'),
                value: Gender.WOMAN,
                groupValue: _gender,
                onChanged: (value) {
                  setState(() {
                    _gender = value;
                  });
                },
              ),
            ],
          ),
        ),
      );
    }
  }
  
  ```
  
---
### 📄test_TextField.dart
  ```
  import 'package:flutter/material.dart';
  
  class TestTextField extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(title: Text('TextField 테스트')),
        body: Padding(
          padding: EdgeInsets.all(16.0),
          child: Column(
            children: [
              TextField(),
              TextField(
                decoration: InputDecoration(labelText: '여기에 입력하세요'),
              ),
              SizedBox(height: 32),
            ],
          ),
        ),
      );
    }
  }
  
  ```

---
### 🖼️화면 출력
  ![1 (1)](https://github.com/user-attachments/assets/a33be731-9e8f-4569-b923-da00a7804483)
  ![2 (1)](https://github.com/user-attachments/assets/5ae20298-cf5b-49c3-a42b-f40eb49d14f8)
  ![3 (1)](https://github.com/user-attachments/assets/61d6e121-0b3c-46b1-b62c-480bb330ee88)
  ![4 (1)](https://github.com/user-attachments/assets/7545d57d-0ab8-4fde-bc63-836d5672d8e9)
  ![5 (1)](https://github.com/user-attachments/assets/9c008b5f-e9e9-419e-8892-8c0ee7333ec0)
