# RAG 검색·벡터 데이터베이스 실습

거리와 유사도 계산부터 문서 청킹, FAISS·Chroma 검색, MMR까지 단계적으로 실습하는 Jupyter 노트북 모음입니다.

## 학습 순서

| 순서 | 자료 | 내용 |
|---|---|---|
| 1 | [검색 기초](%E1%84%80%E1%85%A5%E1%86%B7%E1%84%89%E1%85%A2%E1%86%A8) | 코사인·자카드 유사도, 유클리드·맨해튼 거리 |
| 2 | [청킹 실습](Chunking/chunking_rag.ipynb) | 문자·재귀·토큰 기반 분할, PDF·웹 문서 로딩 |
| 3 | [유사도 검색 통합 실습](Vector_DB/%EC%9C%A0%EC%82%AC%EB%8F%84%EA%B2%80%EC%83%89_%ED%86%B5%ED%95%A9_%EC%B5%9C%EC%8B%A0%EB%B2%84%EC%A0%84.ipynb) | FAISS 인덱스, 텍스트 검색·Q&A, Chroma PDF 검색 |
| 4 | [MMR 비교 실습](Vector_DB/MMR%EA%B2%80%EC%83%89_%EC%B5%9C%EC%8B%A0%EB%B2%84%EC%A0%84.ipynb) | 관련성과 결과 다양성의 균형, retriever 사용 |

`Vector_DB/`의 기존 노트북도 함께 보관합니다. 새로 시작한다면 파일명에 **최신버전**이 붙은 두 검색 노트북부터 사용하세요.

## 실행

Python 3와 독립된 가상환경에서 시작합니다. 저장소 루트에서 실행하세요.

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install jupyterlab numpy scikit-learn
jupyter lab
```

Windows에서는 가상환경 활성화 명령을 `.venv\Scripts\activate`로 바꿉니다.

선택한 노트북의 설치 셀부터 순서대로 실행합니다. 검색 실습의 설치 셀에는 `faiss-cpu`, `langchain-openai`, `langchain-chroma`, `langchain-community`, `pypdf` 등의 의존성이 들어 있습니다.

## API 키와 입력 문서

OpenAI를 호출하는 검색 실습은 `OPENAI_API_KEY`를 환경변수 또는 노트북의 비밀번호 입력 프롬프트로 받습니다. 키를 코드나 출력에 남기지 마세요.

- [MIT.pdf](Chunking/MIT.pdf)는 청킹 예제 자료로 포함되어 있습니다.
- 통합 검색 노트북의 스마트농업·스마트팜 PDF는 별도 준비가 필요합니다. `DATA_DIR`와 PDF 경로를 실제 파일 위치로 바꾸세요.
- 기존 노트북에는 Windows 절대경로와 이전 LangChain import가 남아 있으므로 같은 환경에서 모두 실행된다고 가정하지 않습니다.

API 호출에는 제공자의 사용량 요금이 적용될 수 있습니다.
