# shaman-leading-room-dataset
본 프로젝트는 국내 자산 시장(주식, 가상화폐, 부동산)의 과열 및 변동에 따라 유튜브 플랫폼 내 무속인 채널의 투자 유도 콘텐츠가 어떻게 변화했는지 계량적으로 규명하는 데이터 마이닝 및 데이터 저널리즘 프로젝트입니다.

연구 목적: 자산 시장의 주기적 변동과 비제도권 예측 콘텐츠(무속 투자 방송) 범람 사이의 상관관계를 통계적으로 증명합니다.
분석 대상: 유튜브 내 구독자 5,000명 이상을 보유한 무속인 채널들이 업로드한 동영상 메타데이터.
핵심 질문: 자산 시장이 급등락할 때 무속인의 투자 관련 언급(주식, 코인, 부동산, 금)은 통계적으로 유의미하게 증가하는가? 실제로 2018년 대비 2025년의 증가 폭은 어느 정도인가?

분석 채널 수: 육안 검수를 통해 최종 선별된 무속인 채널 170여 곳
총 수집 영상 수: 151,789개 (2018년 ~ 2026년 7월 업로드 분)

기본 정보: video_id, channel_name, published_at, title, description
성과 지표: view_count, like_count, comment_count
텍스트 마이닝 필터 필드: contains_stock, contains_crypto, contains_gold, contains_real_estate (제목 및 설명란 키워드 매칭 여부를 Boolean 값으로 저장)

주요 분석 기법 및 프로세스
키워드 필터링 및 토픽 분석
형태소 분석: KoNLPy(Kkma/Okt) 패키지를 활용하여 무속 관련 불용어(점사, 신점, 보살 등)를 제거하고 투자 관련 실질 형태소를 추출했습니다.

키워드 사전(Lexicon) 정의:
주식: '주가', '주식', '종목', '상한가', '삼전' 등
코인: '비트코인', '가상화폐', '알트코인', '이더리움' 등
부동산: '아파트', '청약', '재개발', '땅값' 등

├── data/
│   ├── raw_metadata.csv           # 수집된 유튜브 raw 데이터 (비공개 처리)
│   └── refined_trend_summary.csv  # 연도별/월별 집계 통계 데이터
├── notebooks/
│   ├── 01_data_collection.ipynb   # 유튜브 API 활용 데이터 수집 스크립트
│   ├── 02_text_preprocessing.ipynb # KoNLPy 기반 텍스트 정제 및 키워드 라벨링
│   └── 03_trend_visualization.ipynb # 시계열 트렌드 및 통계 시각화 분석
├── src/
│   ├── parser.py                  # 유튜브 데이터 파서 모듈
│   └── utils.py                   # 전처리 유틸리티 함수
├── requirements.txt               # 라이브러리 의존성 파일
└── README.md                      # 프로젝트 안내서

패키지 설
git clone https://github.com/your-username/shaman-investment-trend-analysis.git
cd shaman-investment-trend-analysis
pip install -r requirements.txt

실행 방법
데이터 수집 실행 (API Key 필요):
src/parser.py 파일 내에 본인의 YouTube Data API Key를 설정한 후 실행합니다.
시계열 시각화 생성:
notebooks/03_trend_visualization.ipynb 노트북을 실행하면 연도별 급증세 그래프 및 상관관계 매트릭스를 확인할 수 있습니다.

