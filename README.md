# Tension Reel Study

> Tension Reel 이상 징후 탐지 프로젝트

## 프로젝트 개요
- Tension Reel이란 무엇인가?
  : 4개의 Unit Roll과 중심에 1개의 Mandrel Roll 이라는 설비로 구성됨
  : Strip(열연, 냉연 처리된 최종 얇은 철판)이 EPC(End Point Control) 과정을 통해 Roll 준비를 마침
  : M.R.이 모터구동으로 동작시작 -> U.R.은 Roll 중 Looping(일그러지는 현상) 방지하기 위해 4각에서 잘 말리도록 도움
  : Roll이 완료되면 모터는 off 되며 끝 마감처리를 위해 설비는 Tension off지만 몇 바퀴 더 돎
  
- 프로젝트 목적
  : Roll 과정 중 이상 상태를 조기에 탐지하는 AI 모델 구축

## 진행 일지

### 2025-04-23
- PIMS(Posco Intelligence Maintenance System) 데이터 수집 프로그램으로 데이터 취합
  필요 데이터 : Torque Ref, FBK / Current FBK / Speed Ref, FBK / Tension ON 비트 신호
- 데이터 취합 매커니즘
  설비 데이터 PLC 실시간 업로드 -> 필요 데이터 PLC -> PIMS 연계 주소 값 취합 -> PIMS 상 데이터 SWAB
### 2025-04-24
- Tension Reel의 기본 동작 메커니즘 학습(MCL, HCGL 공정 현장 정비 담당자 interview)
- 설비 이상 상황 파악
  1) Looping -> Tension이 강하게 말리지 않고 느슨하게 말리는 상황
     -> 📚 Looping 현상이 생길 때 모터 상황 요약

        **토크 (Torque)**	  감소 (→) 또는 불안정	릴에 걸리는 장력이 줄어들면서, 필요한 토크가 줄어듬. 때론 토크 변동성 커짐.
        **속도 (RPM)**	    변동성 증가	          감는 속도가 일정해야 하는데, 루프가 생기면서 릴이 "덜 감는" 경향 → 속도 불안정.
        **전류 (Current)**	감소하거나 요동침	    부하 감소로 인해 모터에 필요한 전류가 줄어듬. 하지만 제어계 이슈로 순간적 스파이크도 가능.

### 2025-04-27
- Python으로 초기 데이터 전처리 스크립트 작성
- 이상 데이터 라벨링 방법 고민

---

## 사용 기술
- Python 3.10
- Pandas, Scikit-learn
- PyTorch (학습)
- Matplotlib, Seaborn (시각화용)

## 앞으로 할 일 (TODO)
- 이상탐지 모델 선정
- 모델 학습 및 테스트
- 리포트 작성
