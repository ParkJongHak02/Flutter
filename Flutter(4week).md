# ParkJongHak02 - Flutter


## 4주차 과제
현재 시각을 표시하는 앱


### 코드 정리
'''
import 'package:flutter/material.dart';
import 'dart:async';
import 'package:intl/intl.dart';
import 'package:intl/date_symbol_data_local.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await initializeDateFormatting('ko');
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: '현재 시각',
      home: CurrentTimeScreen(),
    );
  }
}

class CurrentTimeScreen extends StatefulWidget {
  @override
  _CurrentTimeScreenState createState() => _CurrentTimeScreenState();
}

class _CurrentTimeScreenState extends State<CurrentTimeScreen> {
  late Timer _timer;
  DateTime _now = DateTime.now();

  @override
  void initState() {
    super.initState();
    _timer = Timer.periodic(Duration(seconds: 1), (Timer t) {
      setState(() {
        _now = DateTime.now();
      });
    });
  }

  @override
  void dispose() {
    _timer.cancel();
    super.dispose();
  }

  String getFormattedDateTime() {
    String date = DateFormat('yyyy-MM-dd').format(_now);
    String time = DateFormat('a h:mm:ss', 'ko').format(_now);
    return '$date\n$time';
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('현재 시각'),
        centerTitle: true, 
      ),
      body: Center(
        child: Text(
          getFormattedDateTime(),
          textAlign: TextAlign.center,
          style: TextStyle(fontSize: 32),
        ),
      ),
    );
  }
}
'''

'''

'''
'''

'''
