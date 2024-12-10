# gpt-challenge

## Day 1
### Challege
#### ChatOpenAI 모델 초기화 및 설정
ChatOpenAI 생성자를 이용하여 OpenAI의 GPT 모델을 초기화합니다.
model_name 파라미터를 이용하여 모델을 gpt-3.5-turbo 로 지정해줍니다.
streaming=True 옵션과 StreamingStdOutCallbackHandler 콜백을 사용하여 답변 생성 과정을 실시간으로 출력합니다.
#### 프롬프트 템플릿 생성
poet_prompt : 시 생성을 위한 프롬프트 템플릿입니다. {language} 부분은 입력받은 프로그래밍 언어 이름으로 대체됩니다.
explainer_prompt : 시 분석을 위한 프롬프트 템플릿입니다. {poem} 부분은 생성된 시로 대체됩니다.
#### 체인 생성
poet_chain : poet_prompt 템플릿과 chat 모델을 연결하여 시 생성 체인을 만듭니다.
explainer_chain: explainer_prompt 템플릿과 chat 모델을 연결하여 시 분석 체인을 만듭니다.
#### LCEL을 사용하여 체인 연결
final_chain : poet_chain과 explainer_chain을 LCEL (LangChain Expression Language)을 사용하여 연결합니다.
{"poem": poet_chain} : poet_chain의 출력을 poem이라는 변수에 할당하여 explainer_chain에 전달합니다.
#### 최종 체인 실행
final_chain.invoke({"language": "python"}) : final_chain을 실행하여 python이라는 입력 값을 전달합니다. 먼저 poet_chain이 Python에 대한 시를 생성하고, 이 시가 explainer_chain에 전달되어 분석 결과를 출력합니다.
#### 결론
이번 챌린지는 주피터 노트북 환경에서 랭체인 표현 언어(LCEL)를 사용하여 시를 생성하는 체인과 시를 분석하는 체인을 구현하는 과정을 통해 랭체인의 기본적인 사용법을 연습할 수 있는 챌린지였습니다.
<br>
<br>

## Day 2
### 챌린지
#### (EN)
Make a chain that takes the name of a movie and replies with information about the movie such as the director, the main cast, the budget, the box office revenue, the genre of the movie and a small synopsis.
The LLM should always reply using the same format, to accomplish this you must give examples to the LLM of your desired output.
To provide examples use FewShotPromptTemplate or FewShotChatMessagePromptTemplate.
#### (KR)
영화 이름을 가지고 감독, 주요 출연진, 예산, 흥행 수익, 영화의 장르, 간단한 시놉시스 등 영화에 대한 정보로 답장하는 체인을 만드세요.
LLM은 항상 동일한 형식을 사용하여 응답해야 하며, 이를 위해서는 원하는 출력의 예시를 LLM에 제공해야 합니다.
예제를 제공하려면 FewShotPromptTemplate 또는 FewShotChatMessagePromptTemplate을 사용하세요.
<br>
<br>
