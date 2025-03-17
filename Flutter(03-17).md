# 1번
2025.03.17 실습 문제 1번

void main() {
  for (var i = 1; i < 10; i++) {
    for (var j = 1; j < 10; j++) {
      print("$i*$j=${j * i}");
    }
    print("\n");
  }
}


# 2번
void main() {
  var n = 10;

  // 1. 꽉 찬 사각형
  print("꽉 찬 사각형:");
  for (var y = 0; y < n; y++) {
    print("=" * n);
  }

  // 2. 테두리 사각형
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

  // 3. '/' 표시 사각형
  print("\n/ 표시 사각형:");
  for (var y = 0; y < n; y++) {
    var result = "";
    for (var x = 0; x < n; x++) {
      if (x == n - y - 1) {
        result += "/";
      } else {
        result += " ";
      }
    }
    print(result);
  }

  // 4. '\' 표시 사각형
  print("\n\\ 표시 사각형:");
  for (var y = 0; y < n; y++) {
    var result = "";
    for (var x = 0; x < n; x++) {
      if (x == y) {
        result += "\\";
      } else {
        result += " ";
      }
    }
    print(result);
  }

  // 5. 'X' 표시 사각형
  print("\nX 표시 사각형:");
  for (var y = 0; y < n; y++) {
    var result = "";
    for (var x = 0; x < n; x++) {
      if (x == y || x == n - y - 1) {
        result += "X";
      } else {
        result += " ";
      }
    }
    print(result);
  }
}

# 3번
void main() {
  var input = '2025-03-11';

  DateTime date = DateTime.parse(input);

  List<String> days = ['월요일', '화요일', '수요일', '목요일', '금요일', '토요일', '일요일'];

  String nowday = days[date.weekday - 1];

  print('$input의 요일은 $nowday 입니다.');
}
