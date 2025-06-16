# 📘 FocusMate – 스터디 타이머 + 집중 분석 앱

> **Flutter 기반 생산성 향상 앱**  
> 포모도로 기법을 활용한 집중 시간 관리 + 통계 시각화 서비스
   
---
  
# 📅 1주차(9) – 프로젝트 개요 및 전체 기획  

## 🧠 프로젝트 개요

**FocusMate**는 사용자의 공부 또는 작업 시간을 효율적으로 관리할 수 있도록 돕는 **포모도로 타이머** 앱입니다.       
집중 시간 데이터는 기록되고 시각화되어, 사용자가 자신의 집중 패턴을 파악하고 목표를 설정하여 **자기주도적 성장**을 할 수 있도록 합니다.

---

## 🎯 핵심 목표

- **Flutter 숙련도 향상 및 실전 배포 경험**
- **실제로 매일 사용하는 앱 개발 및 유지**
- **취업 포트폴리오로 활용 가능한 완성도 확보**

---

## 🔑 주요 기능

| 기능 | 설명 |
|------|------|
| ⏱ 포모도로 타이머 | 집중(25분)/휴식(5분) 자동 전환 기능 |
| 🧾 집중 기록 | 하루/주간/월간 단위 집중 시간 저장 |
| 📊 집중 통계 시각화 | 그래프 및 차트로 집중 패턴 확인 |
| 🎯 목표 설정 | 일일 집중 목표 및 달성률 계산 |
| 🔔 알림 및 사운드 | 타이머 종료 시 진동/소리/푸시 알림 |
| ☁️ (선택) Firebase 연동 | 사용자 로그인 및 데이터 클라우드 백업 |

---

## 🧱 기술 스택

- **Flutter** – UI 및 앱 전반 구조
- **SharedPreferences** – 로컬 데이터 저장 (기본)
- **Firebase Auth & Firestore** – 사용자 인증 및 클라우드 저장 (선택)
- **fl_chart** – 집중 시간 차트 시각화
- **flutter_local_notifications** – 알림 기능
- **provider** – 상태 관리

---

## 📆 개발 일정 (7주간)

| 주차 | 개발 내용 |
|------|-----------|
| 1주차(9) | 아이디어 구체화, 와이어프레임 및 화면 설계 |
| 2주차(10) | 앱 기본 구조 세팅, 라우팅 및 테마 설정 |
| 3주차(11) | 포모도로 타이머 기능 구현 및 UI 개선 |
| 4주차(12) | 집중 시간 저장 및 로컬 데이터 관리 |
| 5주차(13) | 통계 차트 기능(fl_chart 등) 추가 |
| 6주차(14) | 디자인 정리, Firebase 연동(선택), 사용자 테스트 |
| 7주차(15) | 디버깅, 최종 배포, 발표 자료 정리 및 GitHub 마무리 |

---

## 📌 향후 발전 방향

- 커스터마이징 가능한 타이머 시간 설정
- 친구와 집중 시간 공유 기능
- 다크모드, 위젯 지원

---

## 📂 디렉토리 구조 (예정)

FocusMate/   
├── lib/   
│ ├── screens/   
│ ├── widgets/   
│ ├── models/   
│ ├── services/   
│ └── main.dart    
├── assets/   
├── pubspec.yaml   
├── README.md   


---

# 📅 2주차(10) – 요구사항 목록, 기획 및 설계, 개발 환경 설정

## 📋 요구사항 목록

### ✅ 필수 기능
- 포모도로 타이머 (25/5 분 자동 전환, 시작/일시정지/리셋)
- 오늘의 총 집중 시간 표시
- 집중 세션 기록 저장 (로컬 SharedPreferences 사용)

### ⚙️ 선택 기능
- 집중 시간 통계 그래프 (일/주/월 단위)
- 일일 목표 설정 및 달성률 계산
- Firebase 연동 (로그인, 클라우드 백업)
- 푸시 알림 / 진동 기능
- 다크모드 UI 지원

---

## 🧠 기획 및 설계

### 📱 주요 화면 설계

| 화면 | 구성 요소 |
|------|-----------|
| 홈 화면 | 오늘의 집중 시간, 세션 시작 버튼 |
| 타이머 화면 | 현재 세션 시간, 시작/정지/리셋 버튼 |
| 기록 화면 | 집중 기록 리스트 |
| 분석 화면 (선택) | 집중 시간 그래프 (fl_chart 등 사용) |

---

### 📦 데이터 모델 예시 (로컬 저장용)

```json
{
  "date": "2025-05-19",
  "sessions": [
    { "startTime": "10:00", "duration": 25 },
    { "startTime": "11:00", "duration": 25 }
  ]
}
```
---

# 📅 3주차(11) – 기능 개발 (레이아웃)

## ✅ 이번 주 개발 목표

- 각 기능 화면별 기본 레이아웃 구현
- `BottomNavigationBar`를 통한 탭 구조 완성
- 전체 화면 파일 구조 분리 및 유지보수성 향상

---

## 🖼️ 구현된 화면

| 화면 | 구현 내용 |
|------|-----------|
| **홈 화면** |  
  - 오늘의 누적 집중 시간 표시  
  - “집중 시작” 버튼 구성  
  - 향후 타이머 화면 연결을 위한 구조 확보 |
| **타이머 화면** |  
  - 25분 원형 타이머 UI 구성  
  - 시작 / 일시정지 / 리셋 버튼 구현  
  - 오늘의 집중 시간 표시 영역 구성 |
| **기록 화면** |  
  - 집중 세션 리스트 UI (더미 데이터 기반)  
  - 시작 시각, 날짜, 세션 시간 출력 |
| **통계 화면** |  
  - 일간 / 주간 / 월간 탭 버튼 UI 구성  
  - 통계 차트 출력 영역 확보  
  - 향후 `fl_chart` 연동 준비 완료 |

---

## 🧭 앱 구조 및 네비게이션

- 하단 탭 네비게이션 (`BottomNavigationBar`) 구성 완료  
  → 홈 / 타이머 / 기록 / 통계 4개 탭 연결  
- 각 화면은 `lib/screens/` 하위에 파일로 분리하여 유지보수 편의성 향상  
- `main.dart`는 `MainTabScreen()`을 루트 진입점으로 설정하여 구조 간결화

---

## 📁 디렉토리 구조 (3주차(11) 기준)

lib/   
├── main.dart   
└── screens/   
├── home_screen.dart   
├── timer_screen.dart   
├── record_screen.dart   
├── stats_screen.dart   
└── main_tab_screen.dart   


---

# 📅 4주차(12) – 집중 시간 저장 및 로컬 데이터 관리

## ✅ 이번 주 개발 목표

- 집중 세션 데이터를 앱 종료 후에도 유지되도록 로컬 저장 기능 구현  
- 타이머 종료 시 세션 자동 저장 로직 개발  
- `SharedPreferences` 기반 세션 모델 및 저장 서비스 구축

---

## 💾 데이터 저장 구조

| 파일 | 역할 |
|------|------|
| `focus_session.dart` | 집중 세션 모델 클래스 (날짜, 시작 시각, 집중 시간) |
| `session_storage.dart` | 세션 저장/불러오기 기능 구현 (`SharedPreferences` 사용) |

---

## ⚙️ 구현 기능

- 타이머 종료 시 `_onTimerComplete()` 함수에서 세션 자동 저장
- 저장 시 현재 날짜와 시작 시각, 기본 25분 타이머 정보 포함
- 저장된 세션은 JSON 형태로 로컬에 직렬화 후 보존됨
- 이후 기록 화면 및 통계 화면에서 데이터 연동을 위한 기반 마련 완료

---

## 🧱 주요 코드 흐름

```dart
// 타이머가 0초가 되면 세션을 자동 저장
if (secondsLeft > 0) {
  setState(() => secondsLeft--);
} else {
  _timer?.cancel();
  _onTimerComplete(); // ✅ 이 함수 내에서 저장 처리
  setState(() => isRunning = false);
}
```

---
## 🗂️ 디렉토리 구조 (4주차(12) 기준)

lib/   
├── main.dart     
├── models/   
│   └── focus_session.dart   
├── services/   
│   └── session_storage.dart   
└── screens/   
    ├── home_screen.dart   
    ├── timer_screen.dart   
    ├── record_screen.dart   
    ├── stats_screen.dart   
    └── main_tab_screen.dart   

---

# 📅 5주차(13) – 통계 차트 기능 및 사용자 설정 기능 확장

## ✅ 이번 주 개발 목표

- 집중/휴식 시간 분리 설정 기능 구현 (분+초 단위)
- 집중 목표 시간 설정 및 실시간 달성률 표시
- 휴식 시간 타이머 분리 구현 (자동 전환, 반복)
- 집중/휴식 세션 각각 기록 저장 및 필터링 구현
- 기록 화면 개선: 기록 선택/삭제 및 드롭다운 필터 추가
- `fl_chart` 차트 기반 통계 화면 연동 준비

---

## 🧠 기능 상세 설명

### 🎯 집중 & 휴식 시간 설정 기능

- 홈 화면에서 사용자가 집중/휴식 시간을 각각 **분 + 초 단위**로 설정 가능  
- 설정값은 `SharedPreferences`에 저장되어 앱 재시작 시에도 유지됨

### ⏱ 타이머 개선 – 포모도로 반복 흐름

- **집중 세션 종료 → 알림 → 휴식 시작 버튼 활성화**  
- **휴식 세션 종료 → 알림 → 집중 시작 버튼 활성화**  
- 버튼 클릭을 통해 수동 전환하며 루프 반복 가능

### 🧾 세션 기록 개선

- `FocusSession` 모델에 `type: 'focus' | 'break'` 필드 추가하여 세션 구분  
- 타이머 종료 시 해당 유형에 따라 각각의 세션 기록 자동 저장  
- 기록은 로컬 스토리지에 JSON 형식으로 보존됨

---

## 📋 기록 화면 개선 (RecordScreen)

| 기능 | 설명 |
|------|------|
| ✅ 집중/휴식 구분 | 아이콘 및 라벨로 시각적 구분 |
| 🗂 필터 기능 | 드롭다운으로 `전체 / 집중만 / 휴식만` 보기 |
| 🔄 정렬 기능 | `최신순 / 오래된순` 정렬 토글 |
| ✅ 선택 삭제 | 체크박스로 다중 선택 후 삭제 가능 |
| 🚀 전체 선택/해제 | 모든 기록 일괄 선택/해제 버튼 제공 |

> UI 구성은 `CheckboxListTile`, `DropdownButton`, `PopupMenuButton` 등을 활용하여 사용자 친화적 인터페이스 구현

---

## 📊 통계 화면 연동 준비

- `stats_screen.dart`에 `fl_chart` 적용을 위한 구조 설계  
- 주간/월간 탭 구성 완료  
- 이후 `SessionStorage.loadSessions()` 데이터를 기반으로 차트 출력 예정

---

## 💡 예시 저장 모델 (확장된 세션)

```
json
{
  "date": "2025-06-09",
  "startTime": "10:00",
  "duration": 25,
  "type": "focus"
}
```

---
lib/   
├── main.dart   
├── models/   
│   └── focus_session.dart   
├── services/   
│   └── session_storage.dart   
├── screens/   
│   ├── home_screen.dart   
│   ├── timer_screen.dart   
│   ├── record_screen.dart   
│   ├── stats_screen.dart   
│   └── main_tab_screen.dart     
└── widgets/   
    └── daily_chart_widget.dart  (*예정*)
---
![1](https://github.com/user-attachments/assets/71b1a45a-ed21-4e0c-9809-b14e62b0547b)
![2](https://github.com/user-attachments/assets/e1b6bca8-a39e-4ac6-b3dc-25aa113827f5)
![3](https://github.com/user-attachments/assets/3a508f49-ac87-476e-b125-1d4aaa5a6f57)
![4](https://github.com/user-attachments/assets/feff85b6-85ba-45f7-add0-9c7e1586bf76)

# 📅 6주차(14) – 디자인 개선, 통계 페이지 통합 리디자인, 전체 UI 고도화

## ✅ 이번 주 개발 목표

- 전체 페이지 UI/UX 고급화 (실제 앱처럼 깔끔한 디자인 적용)
- 상단 AppBar 디자인 통일 (`FocusMate - 페이지명`)
- 홈, 타이머, 기록, 통계 화면 디자인 리디자인 완료
- 통계 페이지 내부 구조 정비 및 ChoiceChip 인터랙션 개선

---

## 🎨 전체 UI 통일 작업

| 화면 | 개선 내용 |
|------|----------|
| 홈 화면 | 카드형 레이아웃 적용, 목표 시간 저장 UI 개선, "오늘 기록 초기화" 버튼 디자인 변경 |
| 타이머 화면 | 앱 상단바 삭제, 상단에 커스텀 `FocusMate - 타이머` 상단바 삽입, 타이머 박스 및 버튼 디자인 개선 |
| 기록 화면 | 상단바 통일, 필터 버튼 및 정렬 버튼 디자인 고도화, 기록 없음 상태시 깔끔한 안내문구 적용 |
| 통계 화면 | 상단바 통일, `일간 / 주간 / 월간` ChoiceChip 디자인 개선 및 가운데 정렬 |

---

## 🧭 주요 UI 변경점 (요약)

- 전체 페이지의 상단 AppBar → `FocusMate - [페이지명]` 형태로 통일
- 상단바 색상 통일: `Colors.teal[400]` (기본)
- 텍스트 컬러 통일: 제목 흰색(`Colors.white`), 바디 검정색
- 버튼 컬러 통일: `Colors.teal[300]`, `Colors.orange[300]`
- 카드 형태로 집중 시간 및 설정 정보 감싸기 (`BoxDecoration` 활용)

---

## 📊 통계 페이지 내부 리팩토링

| 기능 | 개선 내용 |
|------|-----------|
| ChoiceChip | 기존 드롭다운 → 상단 중앙 ChoiceChip으로 통일 |
| 시각적 피드백 | 선택된 상태의 컬러 → `Colors.teal[300]` |
| 통계 차트 위젯 | 기존 DailyChartWidget은 유지, StatsScreen에서 통계 페이지 전체 디자인 담당 |
| 상단 제목 제거 | 기존 "집중 및 휴식 시간 통계" 제목 제거로 깔끔한 디자인 확보 |

---

## 🗂️ 디렉토리 구조 (6주차(14) 기준 최종)

lib/   
├── main.dart   
├── models/   
│   └── focus_session.dart   
├── services/   
│   └── session_storage.dart   
├── screens/   
│   ├── home_screen.dart   
│   ├── timer_screen.dart   
│   ├── record_screen.dart   
│   ├── stats_screen.dart   
│   └── main_tab_screen.dart   
└── widgets/   
    ├── daily_chart_widget.dart   
    ├── weekly_chart_widget.dart   
    └── monthly_chart_widget.dart   

---

## 📸 리디자인 결과 예시

> ✅ (이미지 스크린샷들은 발표 자료에서 첨부 예정)

- 홈 화면  
- 타이머 화면  
- 기록 화면  
- 통계 화면

---

## 🔥 현재까지 구현률 요약

- 필수 기능 100% 완료
- UI/UX 리디자인 완료 ✅
- 데이터 저장 / 기록 / 필터링 / 통계 시각화 ✅

---

✅ **다음주 7주차(15)** → 최종 발표 예정

