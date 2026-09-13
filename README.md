# 공유 오피스 서비스 유료 전환 예측

🔗 [Streamlit 앱 바로가기](https://payment-conversion-prediction-kfmzlsbdapywsfresbxfkm.streamlit.app/)

## 개요
- 목표: 3일 무료 체험 후 유료 구독 미전환 고객 조기 식별
  → 전환 가능성이 높은 고객을 미리 파악해 전환 유도 대상 선별에 활용
- 기간: 2026.06.24 ~ 2026.07.03
- 팀: 데이터 분석가 5명
- 데이터: 2021.05 ~ 2023.12 (2년 8개월)
- 분석 대상: 9,110명 (체험 신청 9,659건 → 중복 제거 9,624명 → 방문·출입 기록 불일치 514명 제외), 유료 전환 37.6%

## 내 역할
- 등록·방문·출입·결제 테이블 결합 및 EDA
- 결제 가능 고객을 놓치지 않도록 Recall 중심의 평가 기준 제안

## 분석 단계
1. EDA: 결제율 분석, 방문일수별 패턴
2. Feature Engineering: 9개 → VIF → Ablation Test → 511개 조합 비교(Valid F1) → 3개 (방문일수 · 총출입횟수 · 신청후첫방문일수)
3. Model Comparison: 4개 모델 성능 비교
4. Threshold 조정: 0.45 선택 (Recall 우선, F1 함께 확인)
5. 오류 분석: TP와 FP의 방문 행동이 유사 → 피처 확장 필요

## 최종 모델
XGBoost · Threshold 0.45 · Test 기준

| 메트릭 | 값 |
|--------|-----|
| Recall | 0.9109 |
| Precision | 0.3878 |
| F1 | 0.544 |
| ROC_AUC | 0.5862 |

## 사용 기술
- MySQL, Python (Pandas), Streamlit

## 프로젝트 구조
```
.
├── docs/
│   └── 1. 프로젝트 일정.pdf
│   └── 2. 공유오피스 3일 체험 결제 전환 예측 모델링 보고서.pdf
├── notebooks/
│   ├── 01_prep_eda.ipynb      # 전처리·EDA·모델링 시행착오 기록
│   └── 02_final_report.ipynb  # 정제된 최종 파이프라인·결과 보고서
└── output/
    └── streamlit_screenshot.png
```

> 배포된 Streamlit 앱 코드(`app.py`, 모델 pkl 파일 등)는 별도 저장소([portfolio-02-conversion-prediction-streamlit-app](https://github.com/cannexx/portfolio-02-conversion-prediction-streamlit-app))에서 관리합니다.