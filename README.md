# 공유 오피스 서비스 유료 전환 예측

🔗 [Streamlit 앱 바로가기](https://payment-conversion-prediction-kfmzlsbdapywsfresbxfkm.streamlit.app/)

## 개요
- 목표: 3일 무료 체험 후 유료 구독 미전환 고객 조기 식별
- 기간: 2026.06.24 ~ 2026.07.03
- 데이터: 2021.05 ~ 2023.12

## 분석 단계
1. EDA: 결제율 분석, 방문일수별 패턴
2. Feature Engineering: 9개 → VIF → Ablation Test → 3개
3. Model Comparison: 4개 모델 성능 비교

## 최종 모델
| 메트릭 | 값 |
|--------|-----|
| Recall | 0.9109 |
| Precision | 0.3878 |
| ROC_AUC | 0.5862 |

## 사용 기술
- MySQL, Python (Pandas), Streamlit

## 프로젝트 구조
```
.
├── docs/
│   └── 1. 프로젝트 일정.pdf
├── notebooks/
│   ├── 01_prep_eda.ipynb      # 전처리·EDA·모델링 시행착오 기록
│   └── 02_final_report.ipynb  # 정제된 최종 파이프라인·결과 보고서
└── output/
    └── streamlit_screenshot.png
```

> 배포된 Streamlit 앱 코드(`app.py`, 모델 pkl 파일 등)는 별도 저장소([portfolio-02-conversion-prediction-streamlit-app](https://github.com/cannexx/portfolio-02-conversion-prediction-streamlit-app))에서 관리합니다.