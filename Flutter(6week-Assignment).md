# ParkJongHak02 - Flutter


## 6주차 과제<br/><페이지 203 ~ 208 페이지 내용 실습 및 요약>
위젯의 라이프사이클 확인
<br/>
<br/>
화면의 Stack구조 - push(), pop()시 호출되는 메소드 출력
- initState()
- ispose()
- build()

# 📘 Flutter 위젯 생명주기 실습 요약 (p.203 ~ p.208)

이 리포지토리는 Flutter에서의 화면 전환 및 위젯 생명주기 실습을 정리한 것입니다.  
StatelessWidget과 StatefulWidget의 `build()`, `initState()`, `dispose()` 메서드의 호출 시점을 실습을 통해 확인합니다.

---

## 📌 실습 개요

- `StatelessWidget`과 `StatefulWidget`의 라이프사이클 이해
- 화면 간 전환 시 어떤 메서드가 호출되는지 로그로 확인
- `Navigator.push()` / `Navigator.pop()` 사용 흐름 분석

---

## 🧪 StatelessWidget 실습

### ✅ 핵심 내용
- `build()`는 화면이 표시될 때마다 호출된다.
- 각 화면마다 `build()` 메서드 앞에 `print()`를 추가하여 로그 확인

### 📄 코드 예시
```dart
class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    print('FirstPage build()');
    return Scaffold(...);
  }
}
