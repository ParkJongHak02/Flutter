# ParkJongHak02 - Flutter


## 1주차
안드로이드 스튜디오로 플러터 개발 환경 구성하기, 최초 HelloWorld 앱 실행하기


### 코드 정리
```dart
import 'package:flutter/material.dart';

void main() {
    runApp(const MyApp());
}

class MyApp extends StatelessWidget {
    const MyApp({super.key});

    @override
    Widget build(BuildContext context) {
        return const MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Text(
                        'Hello, World!',
                        style: TextStyle(fontSize: 24),
                    ),
                ),
            ),
        );
    }
}


#### 사진첨부
![스크린샷 2025-03-16 155041](https://github.com/user-attachments/assets/602d2b77-55e0-4a3b-9f80-c60ac4f9f095)

