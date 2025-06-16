# ParkJongHak02 - Flutter


## 5주차


### 수업 정리
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
      ),
      home: MyHomePage(),
    );
  }
}

  class MyHomePage extends StatelessWidget {
    final items = List.generate(100,(i) => i).toList();

    MyHomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
          title: Text('제목')
      ),
      // body: Text('여기에 예제 작성')
      //body: Container(
      //width: 100,
      //height: 100,
      //margin: EdgeInsets.all(80.0),
      //padding: EdgeInsets.all(16.0),
      //color: Colors.blue,
      //child: Text('디모이'),
      //)
      // body: Column(
      //   children: [
      //     Container(
      //     width: 100,
      //     height: 100,
      //     margin: EdgeInsets.all(10.0),
      //     padding: EdgeInsets.all(16.0),
      //     color: Colors.blue,
      //     child: Text('디모일'),
      //     ),
      //     Container(
      //       width: 100,
      //       height: 100,
      //       margin: EdgeInsets.all(10.0),
      //       padding: EdgeInsets.all(16.0),
      //       color: Colors.red,
      //       child: Text('디모이'),
      //     ),
      //     Container(
      //       width: 100,
      //       height: 100,
      //       margin: EdgeInsets.all(10.0),
      //       padding: EdgeInsets.all(16.0),
      //       color: Colors.green,
      //       child: Text('디모삼'),
      //     ),
      //   ],
      // )
      //   body: Row(
      //     children: [
      //       Container(
      //         width: 100,
      //         height: 100,
      //         margin: EdgeInsets.all(10.0),
      //         padding: EdgeInsets.all(16.0),
      //         color: Colors.blue,
      //         child: Text('디모일'),
      //       ),
      //       Container(
      //         width: 100,
      //         height: 100,
      //         margin: EdgeInsets.all(10.0),
      //         padding: EdgeInsets.all(16.0),
      //         color: Colors.red,
      //         child: Text('디모이'),
      //       ),
      //       Container(
      //         width: 100,
      //         height: 100,
      //         margin: EdgeInsets.all(10.0),
      //         padding: EdgeInsets.all(16.0),
      //         color: Colors.green,
      //         child: Text('디모삼'),
      //       ),
      //     ],
      // body: Stack(
      //   children: [
      //     Center(
      //     child: Container(
      //       color: Colors.red,
      //       width: 100,
      //         height: 100,
      //       padding: const EdgeInsets.all(8.0),
      //       margin: const EdgeInsets.all(8.0),
      //     )
      //     ),
      //     Center(
      //         child: Container(
      //           color: Colors.green,
      //           width: 80,
      //           height: 80,
      //           padding: const EdgeInsets.all(8.0),
      //           margin: const EdgeInsets.all(8.0),
      //         )
      //     ),
      //     Center(
      //         child: Container(
      //           color: Colors.blue,
      //           width: 60,
      //           height: 60,
      //           padding: const EdgeInsets.all(8.0),
      //           margin: const EdgeInsets.all(8.0),
      //           child: Center(child:Text('디모이')),
      //         )
      //     ),
      //   ],
      // )
      // body: SingleChildScrollView(
      //   child: ListBody(
      //     children: items.map((i) => Text('$i!!')).toList(),
      //   )
      // )
      // body: ListView(
      //  scrollDirection: Axis.vertical,
      //  children: [
      //    ListTile(
      //      leading: Icon(Icons.home),
      //      title: Text('홈'),
      //      trailing: Icon(Icons.navigate_next),
      //      onTap: () {},
      //    ),
      //    ListTile(
      //      leading: Icon(Icons.event),
      //      title: Text('이벤트'),
      //      trailing: Icon(Icons.navigate_next),
      //      onTap: () {},
      //    ),
      //    ListTile(
      //      leading: Icon(Icons.camera),
      //      title: Text('카메라'),
      //      trailing: Icon(Icons.navigate_next),
      //      onTap: () {},
      //    ),
      //  ],
      // )
      // body: GridView.count(
      //     crossAxisCount: 2,
      //   children: [
      //     Container(
      //       color: Colors.red,
      //       width: 100,
      //         height: 100,
      //       padding: const EdgeInsets.all(80.0),
      //         margin: const EdgeInsets.all(8.0),
      //       child: Text('디모일'),
      //     ),
      //     Container(
      //       color: Colors.green,
      //       width: 100,
      //       height: 100,
      //       padding: const EdgeInsets.all(8.0),
      //       margin: const EdgeInsets.all(8.0),
      //       child: Text('디모이'),
      //     ),
      //     Container(
      //       color: Colors.blue,
      //       width: 100,
      //       height: 100,
      //       padding: const EdgeInsets.all(8.0),
      //       margin: const EdgeInsets.all(8.0),
      //       child: Text('디모삼'),
      //     ),
      //   ]
      // )
      // body: PageView(
      //   children: [
      //     Container(
      //       color: Colors.red,
      //     ),
      //
      //     Container(
      //       color: Colors.green,
      //     ),
      //
      //     Container(
      //       color: Colors.blue,
      //     ),
      //   ],
      // )
      //     body: Text('!'),
      //     bottomNavigationBar: BottomNavigationBar(items: [
      //       BottomNavigationBarItem(
      //           icon: Icon(Icons.home),
      //         label: 'Home',
      //       ),
      //
      //       BottomNavigationBarItem(
      //         icon: Icon(Icons.person),
      //         label: 'profile',
      //       ),
      //
      //       BottomNavigationBarItem(
      //         icon: Icon(Icons.notifications),
      //         label: 'Notification',
      //       ),
      //     ]),
      //   );
      // }

      // body: Center(
      //   child: Text('봄이 왔습니다.'),
      // ),

      //


    //

      // body: SizedBox(
      //   width: 400,
      //   height: 400,
      //   child: Container(
      //     color: Colors.red,
      //   ),
      // ),
    //   body: Center(
    //     child: Card(
    //       shape: RoundedRectangleBorder(
    //         borderRadius: BorderRadius.circular(16.0),
    //       ),
    //       elevation: 4.0,
    // child: Container(
    //  width: 200,
    // height: 200,
    // child: Center(
    // child : Text('생일 축하합니다.'),
    // )
    // )
    //     )
    //   ),
    //   body: Row(
    //     children: [
    //       ElevatedButton(
    //         child: Text('RaisedButton'),
    //         onPressed: () {}
    //       ),
    //       TextButton(
    //         child: Text('TextButton'),
    //         onPressed: () {}
    //       ),
    //       IconButton(
    //         icon: Icon(Icons.add),
    //           color: Colors.red,
    //           iconSize: 100.0,
    //         onPressed: () {}
    //       ),
    //       FloatingActionButton(
    //           child: Icon(Icons.add),
    //           onPressed: () {}
    //       ),
    //     ],
    //   ),

      //body: Image.asset('assets/flutter.png'),
      // body: Icon(
      //   Icons.home,
      //   color: Colors.red,
      //   size: 600.0,
      // )
      

    );
  }

   // );
  // @override
  //   Widget build(BuildContext context) {
  //   return DefaultTabController(
  //     length: 3,
  //     child: Scaffold(
  //       appBar: AppBar(
  //         title: Text('Tab'),
  //         bottom: TabBar(
  //           tabs: [
  //             Tab(icon: Icon(Icons.tag_faces)),
  //             Tab(text: '메뉴'),
  //             Tab(icon: Icon(Icons.info), text: '메뉴3'),
  //           ],
  //         )
  //       ),
  //
  //       body: TabBarView(
  //         children: [
  //           Container(color:  Colors.yellow),
  //           Container(color:  Colors.orange),
  //           Container(color:  Colors.red),
  //         ],
  //       )
  //     )
  //   );
  // }
}

```
### 화면 출력
![1](https://github.com/user-attachments/assets/97ee482a-b220-4d97-b59b-fa42e07d6ea1)
![2](https://github.com/user-attachments/assets/34b1364b-67c3-4136-9c1f-79e6ea246b1b)
![3](https://github.com/user-attachments/assets/8bb9a194-1dba-49e5-ba3f-1c1e43c0a1e1)
![4](https://github.com/user-attachments/assets/ff0ba54d-8f0f-43a4-8b02-78a7fa611c8f)
![5](https://github.com/user-attachments/assets/c2ee5d51-bbae-427c-8be0-e4566d2bc6b1)
![6](https://github.com/user-attachments/assets/f4412e86-f231-43b5-b467-5156a31228fa)
![7](https://github.com/user-attachments/assets/7df8a617-532e-4604-bab1-956aed3fdcd9)
![8](https://github.com/user-attachments/assets/3a8704e3-de91-4d73-afc3-1cc16def25e5)
![9](https://github.com/user-attachments/assets/f2982c52-2ed8-409d-9bc7-b2d0ad486019)
![10](https://github.com/user-attachments/assets/b9628fbf-c98c-4c37-8373-4fb9de75610b)
![11](https://github.com/user-attachments/assets/eb3a1c6e-d266-4aa5-9c2b-c95466dfe73c)
![12](https://github.com/user-attachments/assets/d98f90b5-c77b-404f-9f23-2c74984b94d3)
![13](https://github.com/user-attachments/assets/d8070084-a177-4c59-b121-8bb8720170c2)
![14](https://github.com/user-attachments/assets/1d91c96a-015c-4c6d-bef5-64aff52bd652)
![15](https://github.com/user-attachments/assets/15d5c324-7d34-417b-aa4b-66455255f143)










