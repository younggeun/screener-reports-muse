# screener-reports-muse

주식 스크리너 야간 전 종목 스캔의 로우데이터 저장소. 매일 스캔이 끝나면 결과가 여기에 푸시됩니다.

## 구조

```
scans/
  YYYYMMDD/
    results.csv    # 전 종목 스캔 결과 (로우데이터, 41컬럼)
    summary.json   # 스캔 메타데이터 + 신호 분포
latest.json        # 가장 최근 스캔 날짜 포인터
```

## results.csv 컬럼

| 컬럼 | 설명 |
|---|---|
| session_date | 스캔 기준일 (YYYYMMDD) |
| code | 종목코드 |
| name | 종목명 |
| market | 시장 (KOSPI/KOSDAQ) |
| close_price | 종가 |
| change_ratio | 등락률% |
| sector_name | 섹터 |
| turnover_eok | 당일 거래대금 (억원) |
| average_turnover_20d_eok | 20일 평균 거래대금 (억원) |
| market_cap_won | 시가총액 (원) |
| pivot | 피벗 가격 |
| pivot_dist | 피벗 거리% |
| breakout_distance | 돌파 거리% |
| atr_contraction | ATR 수축% (높을수록 타이트) |
| base_depth | 베이스 깊이% |
| base_weeks | 베이스 기간 (주) |
| latest_volume_ratio | 당일 거래량 / 50일 평균% |
| sepa_score | SEPA 점수 (0-10) |
| vcp_stage | VCP Stage (0-3) |
| vcp_ready | VCP READY 여부 |
| vcp_quality | VCP Quality (0-100) |
| signal | 신호 (돌파완료/돌파임박/수축중/관망/없음/데이터 부족) |
| scan_score | 종합점수 (100점 환산) |
| rs_relative_return | RS 상대수익률 |
| rs_rating | RS 등급 (1-99) |
| ep_date | EP 발생일 |
| ep_gain_percent | EP 상승률% |
| ep_volume_multiple | EP 거래량 배수 |
| ma10_pullback | 10일선 눌림 반등 여부 |
| breakout_precursor | 돌파 전조 여부 |
| breakout_date | 돌파일 |
| breakout_pivot | 돌파 당시 피벗 |
| breakout_close | 돌파일 종가 |
| breakout_volume_ratio | 돌파일 거래량 비율% |
| sr_flip | S/R 플립 여부 |
| sr_flip_level | 플립 레벨 |
| sr_flip_type | 플립 유형 |
| turtle_s1 | 터틀 S1 돌파 여부 |
| turtle_s2 | 터틀 S2 돌파 여부 |
| turtle_stop1 | 터틀 S1 손절가 |
| turtle_stop2 | 터틀 S2 손절가 |

## 참고

- 일봉 OHLCV 원본 캔들(history_json)은 용량 문제로 CSV에서 제외. 스크리너 앱에서 확인 가능.
- 신호별 개수는 summary.json의 signal_distribution 참조.
