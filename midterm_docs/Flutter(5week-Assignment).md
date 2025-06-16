# 🚀 ParkJongHak02 - Flutter


## 📅 5주차 과제 - Flutter 실습 과제
다음과 같은 화면 만들기
<br/>
![스크린샷 2025-04-07 140254](https://github.com/user-attachments/assets/4d6a86a9-9b7a-4954-84ee-f316228b8e0c)
<br/>
계산기 만들기(화면만)
<br/>
![스크린샷 2025-04-07 140300](https://github.com/user-attachments/assets/e6ac4ab1-3c74-4b96-b9e6-cbc31456b9f8)

### 코드 정리
다음과 같은 화면 만들기
```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

class MyHomePage extends StatelessWidget {
  const MyHomePage({super.key, required this.title});

  final String title;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
      ),
      body: Column(
        children: [
          Expanded(
            flex: 2,
            child: Row(
              children: [
                Expanded(
                  flex: 2,
                  child: Container(color: Colors.red),
                ),
                Expanded(
                  flex: 2,
                  child: Column(
                    children: [
                      Expanded(
                        flex: 1,
                        child: Container(color: Colors.blue),
                      ),
                      Expanded(
                        flex: 1,
                        child: Row(
                          children: [
                            Expanded(
                              child: Container(color: Colors.black),
                            ),
                            Expanded(
                              child: Container(color: Colors.orange),
                            ),
                          ],
                        ),
                      ),
                    ],
                  ),
                ),
              ],
            ),
          ),
          Expanded(
            flex: 2,
            child: Container(color: Colors.yellow),
          ),
        ],
      ),
    );
  }
}

```
계산기 만들기(화면만)
```
import 'package:flutter/material.dart';

void main() => runApp(CalculatorApp());

class CalculatorApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: CalculatorScreen(),
    );
  }
}

class CalculatorScreen extends StatelessWidget {
  final List<String> topRow = ['MC', 'MR', 'M+', 'M−', 'MS', 'M˅'];
  final List<List<String>> buttons = [
    ['%', 'CE', 'C', '⌫'],
    ['⅟x', 'x²', '√x', '÷'],
    ['7', '8', '9', '×'],
    ['4', '5', '6', '−'],
    ['1', '2', '3', '+'],
    ['±', '0', '.', '='],
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.black,
      body: SafeArea(
        child: Center(
          child: ConstrainedBox(
            constraints: BoxConstraints(
              maxWidth: 420,
              maxHeight: 800,
            ),
            child: AspectRatio(
              aspectRatio: 0.55,
              child: Column(
                children: [
                  // Custom top bar
                  Padding(
                    padding: const EdgeInsets.symmetric(horizontal: 12, vertical: 10),
                    child: Row(
                      mainAxisAlignment: MainAxisAlignment.spaceBetween,
                      children: [
                        Row(
                          children: [
                            Icon(Icons.menu, color: Colors.white70),
                            SizedBox(width: 10),
                            Text('표준', style: TextStyle(color: Colors.white70, fontSize: 18)),
                            SizedBox(width: 6),
                            Icon(Icons.crop_square, color: Colors.white70, size: 16),
                          ],
                        ),
                        Icon(Icons.history, color: Colors.white70),
                      ],
                    ),
                  ),
                  Expanded(
                    flex: 2,
                    child: Container(
                      alignment: Alignment.bottomRight,
                      padding: EdgeInsets.all(20),
                      child: Text(
                        '0',
                        style: TextStyle(color: Colors.white, fontSize: 48),
                      ),
                    ),
                  ),
                  Row(
                    children: topRow
                        .map((label) => Expanded(
                      child: Container(
                        padding: EdgeInsets.symmetric(vertical: 6),
                        alignment: Alignment.center,
                        child: Text(
                          label,
                          style: TextStyle(color: Colors.white70, fontSize: 18),
                        ),
                      ),
                    ))
                        .toList(),
                  ),
                  Expanded(
                    flex: 13,
                    child: Column(
                      children: buttons.map((row) {
                        return Expanded(
                          child: Row(
                            children: row.map((label) {
                              return Expanded(
                                child: Container(
                                  margin: EdgeInsets.all(1),
                                  child: ElevatedButton(
                                    onPressed: () {},
                                    style: ElevatedButton.styleFrom(
                                      padding: EdgeInsets.zero,
                                      backgroundColor: Colors.grey[900],
                                      foregroundColor: Colors.white,
                                      shape: RoundedRectangleBorder(
                                        borderRadius: BorderRadius.circular(6),
                                      ),
                                    ),
                                    child: Center(
                                      child: Text(
                                        label,
                                        style: TextStyle(fontSize: 22),
                                      ),
                                    ),
                                  ),
                                ),
                              );
                            }).toList(),
                          ),
                        );
                      }).toList(),
                    ),
                  ),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}

```
### 화면 출력
다음과 같은 화면 만들기
![스크린샷 2025-04-07 141442](https://github.com/user-attachments/assets/d5be42fa-527b-434c-996a-23e4fd4af826)
계산기 만들기(화면만)
![스크린샷 2025-04-07 144228](https://github.com/user-attachments/assets/d8b17ddf-22ca-4374-a3ec-880d15dee89d)
