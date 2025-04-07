# ParkJongHak02 - Flutter


## 5주차 과제
다음과 같은 화면 만들기
<br/>
![스크린샷 2025-04-07 140254](https://github.com/user-attachments/assets/4d6a86a9-9b7a-4954-84ee-f316228b8e0c)
<br/>
![스크린샷 2025-04-07 140300](https://github.com/user-attachments/assets/e6ac4ab1-3c74-4b96-b9e6-cbc31456b9f8)

### 코드 정리
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
### 화면 출력
![스크린샷 2025-04-07 141442](https://github.com/user-attachments/assets/d5be42fa-527b-434c-996a-23e4fd4af826)
