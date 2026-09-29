# InspectorsAlly - TensorFlow/Keras

가죽 제품 이미지를 입력받아 정상·불량을 분류하고, 결함이 의심되는 영역을 CAM 히트맵과 경계 상자로 보여주는 Streamlit 검사 애플리케이션입니다.

## 주요 기능

- 이미지 업로드 또는 카메라 촬영 입력
- VGG16 전이학습 모델을 이용한 정상·불량 이진 분류
- 클래스별 예측 확률 표시
- CAM 기반 결함 의심 영역 시각화
- Streamlit 기반 웹 UI

## 기술 스택

- Python 3.10
- TensorFlow 2.17 / Keras
- Streamlit
- NumPy, Matplotlib, Pillow

## 프로젝트 구조

```text
.
├── tf_App_keras.py              # Streamlit 애플리케이션
├── weights/leather_model.keras  # 모델 구조와 가중치
├── requirements.txt             # 실행 의존성
└── packages.txt                 # 배포 환경 시스템 패키지
```

## 실행 방법

```bash
python -m venv .venv
```

가상환경을 활성화한 뒤 다음 명령을 실행합니다.

```bash
pip install -r requirements.txt
streamlit run tf_App_keras.py
```

## 모델 입력과 출력

| 항목 | 내용 |
|---|---|
| 입력 | RGB 이미지, 224 x 224 |
| 백본 | ImageNet 사전학습 VGG16 |
| 출력 | Sigmoid 기반 불량 확률 |
| 판정 | 0.5 초과 시 불량 |
| 설명 가능성 | 마지막 합성곱 특성맵 기반 CAM |

## 참고

교육 프로젝트에서 구축한 프로토타입입니다. 실제 생산 검사에 적용하려면 현장 데이터로 정확도와 임계값을 다시 검증하고, 조명·카메라 조건에 따른 성능 편차를 확인해야 합니다.
