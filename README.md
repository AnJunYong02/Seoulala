# 🗺️ 서울 관광지 추천 AI 챗봇 - Seoulala

**Seoulala**는 LangChain과 Azure OpenAI를 기반으로 한 **서울 관광지 추천 AI 챗봇**이다.
Streamlit 인터페이스를 통해 사용자가 입력한 여행 목적이나 상황(예: 비 오는 날, 가족과 함께 등)에 따라 서울에 있는 관광지를 실시간 날씨에 맞춰 추천해준다.

---
## 🌄 실행 화면
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/4db1d69f-5377-4066-ae00-24aa723a7c23" />
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/e005f8d3-9b06-40d0-a9f5-a81d4b6056a4" />
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/c08096c0-65ee-4dae-8d04-1f0184a8fe83" />

---
## 🌟 주요 기능

### ✅ 사용자 맞춤 관광지 추천
- 사용자의 여행 목적에 맞게 **서울 관광지 JSON 데이터**에서 알맞은 장소를 추천
- **날씨에 따라 실내/실외 장소를 구분하여 추천**

### ✅ 하이브리드 검색 + 재랭킹
- **BM25와 Vector 검색을 결합**한 Hybrid Retriever로 보다 정교한 검색 결과 제공
- **LLM Listwise Reranker**를 통해 Top-N 결과를 재정렬

### ✅ Tool-Calling 기반 멀티 툴 연동
- `get_weather`: OpenWeatherMap API를 이용해 **서울의 실시간 날씨** 정보를 가져옴
- `search_tour_place`: 사용자의 쿼리에 따라 **관광지 정보 검색 및 재구성된 설명 제공**

### ✅ LangChain + Azure OpenAI 기반 에이전트
- GPT-4.1 기반 LLM을 사용하여 자연스럽고 논리적인 추천 생성
- Embedding은 `text-embedding-3-small`을 사용하여 관광지 데이터를 벡터화

### ✅ Streamlit UI
- 직관적인 웹 UI
- `@st.cache_*`을 사용한 리소스 캐싱으로 **빠른 반응 속도** 제공

---

## 🧰 기술 스택

| 항목        | 내용                                           |
|-------------|------------------------------------------------|
| 언어         | Python                                         |
| 웹 프레임워크 | Streamlit                                     |
| LLM         | Azure OpenAI (GPT-4.1, GPT-4o-mini)             |
| 검색엔진     | BM25 + ChromaDB Vector Store (Ensemble)        |
| 재랭커       | LangChain `LLMListwiseRerank`                  |
| 임베딩 모델  | `text-embedding-3-small` from Azure OpenAI     |
| 외부 API     | OpenWeatherMap (날씨 데이터 수집)              |
| 데이터       | 서울 관광지 JSON (`seoul_tour_clean.json`)     |

---

## 🗃️ 실행 방법

1. <.env파일>에 key 값들 등록
2. pip install -r requirements.txt => 패키지 설치
3. streamlit run Seoulala.py => Streamlit 실행
