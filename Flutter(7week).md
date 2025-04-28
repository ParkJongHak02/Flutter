# ParkJongHak02 - Flutter


## 7주차


### 수업 중 코드정리(a_7_1)
main.dart
```
import 'package:flutter/material.dart';
import 'package:a_7_1/page1.dart';
import 'package:a_7_1/page2.dart';
import 'package:a_7_1/page3.dart';

final dummyItems = [
  'https://cdn.pixabay.com/photo/2018/11/12/18/44/thanksgiving-3811492_1280.jpg',
  'https://cdn.pixabay.com/photo/2019/10/30/15/33/tajikistan-4589831_1280.jpg',
  'https://cdn.pixabay.com/photo/2019/11/25/16/15/sfari-4652364_1280.jpg',

];

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: '복잡한 ui작성',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.orange),
      ),
      home: const MyHomePage(),
      debugShowCheckedModeBanner: false,
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key});

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  var _index = 0;
  var _pages = [Page1(), Page2(), Page3()];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.white,
        title: Text('복잡한 ui', style: TextStyle(color: Colors.black)),
        centerTitle: true,
        actions: [
          IconButton(
            icon: Icon(Icons.add, color: Colors.black),
            onPressed: () {},
          ),
        ],
      ),
      // body: Center(child: Text('$_index 페이지', style: TextStyle(fontSize: 40))),
      body: _pages[_index],
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _index,
        items: [
          BottomNavigationBarItem(label: '홈', icon: Icon(Icons.home)),
          BottomNavigationBarItem(label: '이용서비스', icon: Icon(Icons.assignment)),
          BottomNavigationBarItem(
            label: '내 정보',
            icon: Icon(Icons.account_circle),
          ),
        ],
        onTap: (index) {
          setState(() {
            _index = index;
          });
        },
      ),
    );
  }
}
```
page1.dart
```
import 'package:a_7_1/main.dart';
import 'package:flutter/material.dart';
import 'package:carousel_slider/carousel_slider.dart';

class Page1 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(8.0),
      child: ListView(
        children: [
        _buildTop(),
          SizedBox(height: 16),
          _buildMiddle(),
          SizedBox(height: 16),
          _buildBottom(),

        ],
      ),
    );
    return ListView(children: [_buildTop(), _buildMiddle(), _buildBottom()]);
  }

  Widget _buildTop() {
    return Column(
      children: [
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            _buildTaxiMenu(),
            _buildTaxiMenu(),
            _buildTaxiMenu(),
            _buildTaxiMenu(),
          ],
        ),
        SizedBox(height: 20),
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            _buildTaxiMenu(),
            _buildTaxiMenu(),
            _buildTaxiMenu(),
            _buildTaxiMenu(visible: false),
          ],
        ),
      ],
    );
  }

  Widget _buildTaxiMenu({bool visible = true}) {
    return Opacity(
      opacity: visible ? 1.0 : 0.0,
      child: InkWell(
        onTap: () {},
        child: Column(children: [Icon(Icons.local_taxi, size: 40), Text('택시')]),
      ),
    );
  }

  Widget _buildMiddle() {
    return CarouselSlider(
      items:
          dummyItems.map((url) {
            return Builder(
              builder: (BuildContext context) {
                return Container(
                  width: MediaQuery.of(context).size.width,
                  margin: EdgeInsets.symmetric(horizontal: 5.0),
                  child: Image.network(url, fit: BoxFit.cover),
                );
              },
            );
          }).toList(),

      options: CarouselOptions(height: 150.0, autoPlay: true),
    );
  }

  Widget _buildBottom() {
    final items = List.generate(10, (i) {
      return ListTile(
        leading: Icon(Icons.notifications_none),
        title: Text('[이벤트]이것은 공지사항 $i입니다.'),
      );
    });

    return ListView(
      physics: NeverScrollableScrollPhysics(),
      children: items,
        shrinkWrap: true,
    );
  }
}
```
page2.dart
```
import 'package:flutter/material.dart';

class Page2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(child: Text('이용서비스', style: TextStyle(fontSize: 40)));
  }

}
```
page3.dart
```
import 'package:flutter/material.dart';

class Page3 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(child: Text('내 정보', style: TextStyle(fontSize: 40)));
  }

}
```
pubspec.yaml
```
name: a_7_1
description: "A new Flutter project."
# The following line prevents the package from being accidentally published to
# pub.dev using `flutter pub publish`. This is preferred for private packages.
publish_to: 'none' # Remove this line if you wish to publish to pub.dev

# The following defines the version and build number for your application.
# A version number is three numbers separated by dots, like 1.2.43
# followed by an optional build number separated by a +.
# Both the version and the builder number may be overridden in flutter
# build by specifying --build-name and --build-number, respectively.
# In Android, build-name is used as versionName while build-number used as versionCode.
# Read more about Android versioning at https://developer.android.com/studio/publish/versioning
# In iOS, build-name is used as CFBundleShortVersionString while build-number is used as CFBundleVersion.
# Read more about iOS versioning at
# https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html
# In Windows, build-name is used as the major, minor, and patch parts
# of the product and file versions while build-number is used as the build suffix.
version: 1.0.0+1

environment:
  sdk: ^3.7.2

# Dependencies specify other packages that your package needs in order to work.
# To automatically upgrade your package dependencies to the latest versions
# consider running `flutter pub upgrade --major-versions`. Alternatively,
# dependencies can be manually updated by changing the version numbers below to
# the latest version available on pub.dev. To see which dependencies have newer
# versions available, run `flutter pub outdated`.
dependencies:
  flutter:
    sdk: flutter

  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^1.0.8
  carousel_slider: ^5.0.0

dev_dependencies:
  flutter_test:
    sdk: flutter

  # The "flutter_lints" package below contains a set of recommended lints to
  # encourage good coding practices. The lint set provided by the package is
  # activated in the `analysis_options.yaml` file located at the root of your
  # package. See that file for information about deactivating specific lint
  # rules and activating additional ones.
  flutter_lints: ^5.0.0

# For information on the generic Dart part of this file, see the
# following page: https://dart.dev/tools/pub/pubspec

# The following section is specific to Flutter packages.
flutter:

  # The following line ensures that the Material Icons font is
  # included with your application, so that you can use the icons in
  # the material Icons class.
  uses-material-design: true

  # To add assets to your application, add an assets section, like this:
  # assets:
  #   - images/a_dot_burr.jpeg
  #   - images/a_dot_ham.jpeg

  # An image asset can refer to one or more resolution-specific "variants", see
  # https://flutter.dev/to/resolution-aware-images

  # For details regarding adding assets from package dependencies, see
  # https://flutter.dev/to/asset-from-package

  # To add custom fonts to your application, add a fonts section here,
  # in this "flutter" section. Each entry in this list should have a
  # "family" key with the font family name, and a "fonts" key with a
  # list giving the asset and other descriptors for the font. For
  # example:
  # fonts:
  #   - family: Schyler
  #     fonts:
  #       - asset: fonts/Schyler-Regular.ttf
  #       - asset: fonts/Schyler-Italic.ttf
  #         style: italic
  #   - family: Trajan Pro
  #     fonts:
  #       - asset: fonts/TrajanPro.ttf
  #       - asset: fonts/TrajanPro_Bold.ttf
  #         weight: 700
  #
  # For details regarding fonts from package dependencies,
  # see https://flutter.dev/to/font-from-package
```

### 화면 출력
![1 (1)](https://github.com/user-attachments/assets/82b5ed55-21f1-4365-846a-db9f31a5fe36)
![2 (1)](https://github.com/user-attachments/assets/29ee9bdc-e490-485a-8557-608f2673bf81)
![3 (1)](https://github.com/user-attachments/assets/ca610e5e-b988-4791-b46a-24f137676cd0)
![4 (1)](https://github.com/user-attachments/assets/77b6eb99-fff7-4840-b54a-28099388e395)
![5 (1)](https://github.com/user-attachments/assets/1ae9889f-b028-487e-98de-57557e0d5bdd)
![6 (1)](https://github.com/user-attachments/assets/28ca384f-c3f4-4388-88ed-05f17b37a469)
![7 (1)](https://github.com/user-attachments/assets/ca12e048-ff8d-4fde-83de-d8bcb9ee6d1a)
![8](https://github.com/user-attachments/assets/4c33e9a2-ba9d-4504-afac-0fdad1d06a60)
![9](https://github.com/user-attachments/assets/686d1733-3a09-4a71-820a-f4ebdc077d69)
![10](https://github.com/user-attachments/assets/bea4aed4-dfb6-4d74-95ed-943ceaeea1a5)
![11](https://github.com/user-attachments/assets/61ee45ac-f8c9-4334-840c-0b4325812351)
![12](https://github.com/user-attachments/assets/aee4b8e5-30d7-4297-a7c6-6e6a6b364ad1)
