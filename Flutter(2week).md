# ParkJongHak02 - Flutter


## 2주차


### 실습 1번
```
void main() {
  for (var i = 1; i < 10; i++) {
    for (var j = 1; j < 10; j++) {
      print("$i*$j=${j * i}");
    }
    print("\n");
  }
}
```

### 실습 2번
```
void main() {
  var n = 10;

  // 1. 꽉 찬 사각형
void main() {
  var n = 10;

print("꽉 찬 사각형:");
  for (var y = 0; y < n; y++) {
    print("=" * n);
  }
}

  // 2. 테두리 사각형
void main() {
  var n = 10;

  print("\n테두리 사각형:");
  for (var y = 0; y < n; y++) {
    var result = "";
    for (var x = 0; x < n; x++) {
      if (y == 0 || y == n - 1 || x == 0 || x == n - 1) {
        result += "=";
      } else {
        result += " ";
      }
    }
    print(result);
  }
}

  // 3. '/' 표시 사각형
void main() {
  var n = 10;

  print("\n/ 표시 사각형:");
  for (var y = 0; y < n; y++) {
    var result = "";
    for (var x = 0; x < n; x++) {
      // 테두리 조건
      if (y == 0 || y == n - 1 || x == 0 || x == n - 1) {
        result += "=";
      } 
      // 대각선 조건 (우측 상단 -> 좌측 하단)
      else if (x == n - 1 - y) {
        result += "/";
      } 
      else {
        result += " ";
      }
    }
    print(result);
  }
}


  // 4. '\' 표시 사각형
void main() {
  var n = 10;

  print("\n\\ 표시 사각형:");
  for (var y = 0; y < n; y++) {
    var result = "";
    for (var x = 0; x < n; x++) {
      // 테두리 조건
      if (y == 0 || y == n - 1 || x == 0 || x == n - 1) {
        result += "=";
      }
      // 대각선 조건 (좌측 상단 -> 우측 하단)
      else if (x == y) {
        result += "\\";
      } 
      else {
        result += " ";
      }
    }
    print(result);
  }
}


  // 5. 'X' 표시 사각형
void main() {
  var n = 10;

  print("\n테두리 사각형:");
  for (var y = 0; y < n; y++) {
    var result = "";
    for (var x = 0; x < n; x++) {
      // 테두리 조건
      if (y == 0 || y == n - 1 || x == 0 || x == n - 1) {
        result += "=";
      }
      // 대각선 조건 (우측 상단 -> 좌측 하단)
      else if (x == n - 1 - y) {
        result += "/";
      }
      // 대각선 조건 (좌측 상단 -> 우측 하단)
      else if (x == y) {
        result += "\\";
      } 
      else {
        result += " ";
      }
    }
    print(result);
  }
}

```
### 실습 3번
```
void main() {
  String input = '2025-03-11'; // 입력값
  List<String> weekdays = ['월', '화', '수', '목', '금', '토', '일'];

  // 입력 문자열을 DateTime 객체로 변환
  DateTime date = DateTime.parse(input);

  // DateTime의 weekday는 1(월요일)부터 7(일요일)까지 반환
  String result = weekdays[date.weekday - 1]; // 배열의 인덱스는 0부터 시작

  print(result); // 요일 출력
}
```
