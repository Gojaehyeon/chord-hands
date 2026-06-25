# 🎹 HandChord — 손으로 연주하는 코드 신스

> **패스트캠퍼스(FastCampus) 강의자료입니다.**
> 본 프로젝트는 패스트캠퍼스 강의 실습용으로 제작된 교육 자료입니다.

웹캠으로 **양손을 추적**해, 손 위치로 코드를 골라 신스(기계음)로 연주하는 웹 악기입니다.
별도 설치나 빌드 없이 `index.html` 하나로 동작합니다.

## ✨ 동작 방식

- **왼손 → 왼쪽 휠**: `C D E F G A B` 7개 루트 음을 원형 섹터에서 선택
- **오른손 → 오른쪽 휠**: **가운데 원 = 기본(메이저 트라이어드)**, 둘러싼 8개 섹터 = `m / M7 / m7 / 7 / sus4 / sus2 / dim / add9`
- 양손이 모두 휠 위에 있으면 → `루트 + 종류` 코드가 연주되고, 선택을 바꾸면 부드럽게 글라이드
- **핀치(엄지+검지)** = 스트럼(액센트로 다시 튕김)
- 소리는 Web Audio API로 합성한 **기계음 신스** (saw + square 디튠 + 로우패스 + 딜레이)

## 🚀 실행 방법

카메라 권한 때문에 `localhost` 또는 `https`로 띄워야 합니다 (`file://`는 브라우저가 카메라를 차단합니다).

```bash
git clone https://github.com/Gojaehyeon/chord-hands.git
cd chord-hands
python3 -m http.server 8000
# 브라우저에서 http://localhost:8000 접속 → "시작하기" → 카메라 허용
```

> 밝은 단색 배경에서 손이 잘 인식됩니다. 화면 기준 **왼손은 왼쪽 / 오른손은 오른쪽**에 두세요.
> 첫 실행 시 MediaPipe 손 인식 모델을 CDN에서 내려받으므로 인터넷 연결이 필요합니다.

## 🛠 기술 스택

| 영역 | 사용 기술 |
|------|-----------|
| 손 추적 | [MediaPipe Tasks Vision](https://developers.google.com/mediapipe) `HandLandmarker` (양손, GPU) |
| 소리 합성 | Web Audio API (오실레이터 직접 신시사이즈) |
| 렌더링 | HTML5 Canvas + 웹캠 미러 배경 |
| 빌드 | 없음 — 의존성 없는 단일 HTML 파일 |

## 📄 라이선스

교육 목적의 패스트캠퍼스 강의자료입니다. 자유롭게 학습·실습에 활용하세요.
