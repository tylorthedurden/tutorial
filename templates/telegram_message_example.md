# Telegram Message Examples

## Example 1

```
https://www.inceptionlabs.ai/

"Diffusion 기반 Language Model 첫 상용화 미국 스타트업 Inception Labs"

최근 Diffusion 기반 Language Model의 연구가 활발하게 이루어지고 있는 가운데 이를 상용화한 미국 스타트업이 최근 이슈가 되고 있습니다.

# 주요 멤버

- Stanford 교수인 Stefano Ermon / Cornell Tech 교수인 Voiodymyr Kuleshov 등 학계 저명인사로 구성
- 기술 연구 역량에 있어서 세계 최고 수준의 역량 보유

- 현재 AI 분야 연구에서 주목할만한 업적으로 평가 받는 특히 Flash Attention / DPO 등 현재 AI 개발의 핵심적 기술로 평가받는 

# 기술 경쟁력

그들이 공개한 Mercury 모델 (Small, Mini 2가지 Version)은 생성 속도에 있어서 기존 순차적 방식인 Transformer 기반 모델 대비 월등한 수준을 보여주고 있습니다. (5 ~ 10배)

이러한 속도에도 모델의 정확도 성능에 있어서 Leading AI Tech 기업 (OpenAI / Anthropic / Google)의 경량 모델과 Coding 성능에서 유사한 수준을 보여주고 있어서 경쟁력 있는 대안으로 평가 받고 있습니다.

# 당사 시너지 가능성

- Multi LLM 경쟁력 강화를 위한 기술 Diversity 확보
   " 생성 속도 측면에서 강점이 있는 LLM 제휴를 통해 Platform을 통한 LLM 공급 및 Telco LLM 활용"
- Agent Action (Tool Use / Function Calling) 측면의 대체제 검토
   " Code 및 Structured Output 생성에 강점이 있으며 특히 생성 속도에 기존 동등 규모 모델 대비 5 ~ 10배, 현재 Agent Action의 고질적인 문제점인 속도를 비약적으로 개선할 수 있을 것으로 기대"
```

## Example 2

```
https://arxiv.org/pdf/2502.11089


tl;dr;
NSA, DeepSeek에서 공개한 새로운 Attention 알고리즘 (LLM의 기반 알고리즘) 기술, 모델 개발 속도 최대 9배 향상 (결국 비용 절감)



기존의 Attention의 Sparsity(정보의 희소성)를 보다 효과적으로 활용할 수 있는 알고리즘으로 이에 GPU에 추가적인 최적화 (Memory Loading 효율화)를 통해

Long Context (긴 Reasoning 과정)에서 학습 속도 약 6배 이상 향상 / 추론 속도 11배 향상 / 특히 긴 Context에서의 정확도 향상을 보였습니다.

이를 통해 기존 효율성 측면에서의 경쟁력을 더욱 압도적인 수준으로 가져갈 것으로 예상되며 2Q에 예고된 DeepSeek R1 후속 모델을 통해 이러한 차별화된 기술의 결과를 경험해볼 수 있을 것으로 예상됩니다.

## Implication
- Reasoning Model의 개발 비용 및 운영 비용의 지속적인 절감 예상
- 비용 및 성능 최적화 기술의 지속적인 혁신을 통해 대규모 투자 기반의 미국 Frontier Lab 대비 개발 속도 및 비용 측면의 경쟁력을 확보, 향후 기술 우위를 위한 발판을 마련


## 상세

### 문제
- 기존 Attention 알고리즘은 Attention의 Sparsity (중요한 정보는 일부이고 나머지는 필요 없거나 중요도가 낮은 점보) 기반의 최적화에 한계가 있었음
- 그리고 이러한 최적화 기술들은 추론 혹은 학습 어느 한쪽에 최적화되어 있었고
- 그러다 보니 추론에서 Sparsity 최적화를 적용할 수 있다 하더라도 Long Context (길이가 긴 텍스트 데이터)를 학습하는데 한계가 있었음
- 이러한 이유로 실제 Test-Time Scaling을 통해서 Reasoning (Thinking)을 하더라도 충분한 효과를 내지 못하는 문제가 있었음

### 접근
- Attention의 K,V를 Block이라는 고정된 크기의 더 조밀한 정보 형태로 압축 (Sparsity가 있기 때문에 압축이 가능)
- 이 고정된 압축된 Block 중 Next Token 예측에 유의미한 즉, Attention Weight가 큰 것들을 선별
- 이 선별된 Block에 포함된 Token들 그리고 압축된 Block 등 상대적으로 적은양의 정보를 활용하도록 Attention을 구현
- 추가로 이 고정 크기의 Block을 GPU의 Memory Access에 최적화되도록 설계함

### 결과
- Needle In Haystack (바늘찾기 Benchmarking으로 Context에 정보 위치를 변경하고 해당 정보에 대한 질의에 정답을 맞추는지 확인)애서 100%의 정확도
- 추론 시 11배 속도 향상
- 학습 시 Forward 9배 / Backward 6배 속도 향상
- 게다가 몇가지 Benchmark에서 정확도도 향상됨을 확인
```
