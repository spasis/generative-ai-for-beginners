# 다양한 LLM 탐색 및 비교

[![Exploring and comparing different LLMs](../../images/02-lesson-banner.png?WT.mc_id=academic-105485-koreyst)](https://youtu.be/J1mWzw0P74c?WT.mc_id=academic-105485-koreyst)

> *본 강의에 대한 동영상을 보려면 위의 이미지를 클릭하세요.*

이전 단원에서는 생성형 AI가 기술 환경을 어떻게 변화시키고 있는지, 대규모 언어 모델(LLM)이 어떻게 작동하는지, 스타트업과 같은 비즈니스가 이를 사용 사례에 적용하고 성장하는 방법을 살펴보았습니다! 이번 장에서는 다양한 유형의 대규모 언어 모델(LLM)을 비교하고 대조하여 장단점을 이해하고자 합니다.

우리 스타트업 여정의 다음 단계는 현재 대규모 언어 모델(LLM)의 환경을 살펴보고 어떤 것이 우리의 사용 사례에 적합한지 이해하는 것입니다.

## 개요

이 강좌에서는 다음을 다룹니다:

- 현존하는 다양한 유형의 LLM.
- Azure에서 사용 사례에 대한 다양한 모델을 테스트, 반복 및 비교하기.
- LLM을 배포하는 방법.

## 학습 목표

이 강좌를 완료하면 다음을 수행할 수 있습니다:

- 사용 사례에 적합한 모델을 선택.
- 모델의 성능을 테스트, 반복 및 개선하는 방법을 이해.
- 비즈니스에서 모델을 배포하는 방법을 이해.

## 다양한 유형의 LLM 이해

대규모 언어 모델(LLM)은 아키텍처, 학습 데이터 및 사용 사례에 따라 여러 가지로 분류할 수 있습니다. 이러한 차이점을 이해하면 스타트업이 비즈니스 시나리오에 적합한 모델을 선택하고 테스트, 반복 및 성능 개선 방법을 이해하는 데 도움이 됩니다.

LLM 모델에는 다양한 유형이 있으며, 사용 목적, 데이터, 지불할 수 있는 예산 등에 따라 모델을 선택할 수 있습니다.

텍스트, 오디오, 비디오, 이미지 생성 등에 모델을 사용하려는 목적에 따라 적합한 유형의 모델을 선택할 수 있습니다.

- **오디오 및 음성 인식(Audio and speech recognition)**. 음성 인식을 목적으로 한다면 Whisper-type 모델은 범용적면서도 우수한 모델입니다. 다양한 오디오에 대해 학습되어 다국어 음성 인식을 수행할 수 있습니다. [여기](https://platform.openai.com/docs/models/whisper?WT.mc_id=academic-105485-koreyst)에서 Whisper-type 모델에 대해 자세히 알아보세요.

- **이미지 생성(Image generation)**. 이미지 생성을 목적으로 한다면,  DALL-E와 Midjourney가 좋은 선택지가 될 수 있습니다. DALL-E는 Azure OpenAI에서 제공합니다. DALL-E에 대한 자세한 내용은 [여기](https://platform.openai.com/docs/models/dall-e?WT.mc_id=academic-105485-koreyst)와 이 커리큘럼의 9장에서 확인하세요.

- **텍스트 생성(Text generation)**. 대부분의 모델은 텍스트 생성에 대해 학습되어 있으며 GPT-3.5부터 GPT-4까지 다양한 선택이 가능합니다. 각 모델마다 비용이 다르며 GPT-4가 가장 비쌉니다. 기능 및 비용 측면에서 요구 사항에 가장 적합한 모델을 평가하려면 [Azure Open AI playground](https://oai.azure.com/portal/playground?WT.mc_id=academic-105485-koreyst)를 살펴보는 것이 좋습니다.

모델을 선택하면 몇 가지 기본 기능을 사용할 수 있지만 그것만으로는 충분하지 않을 수 있습니다. 종종 LLM에 어떻게든 제공해야 하는 회사의 특수한 데이터가 있는 경우가 있습니다. 이에 접근하는 방법에는 몇 가지 다른 선택지가 있으며, 이에 대해서는 다음 섹션에서 자세히 설명합니다.

### 파운데이션 모델 vs. LLMs

파운데이션 모델(foundation model)이라는 용어는 스탠포드 연구진이 만든 것으로, 다음과 같은 몇 가지 기준을 따르는 AI 모델로 정의됩니다:

- **비지도 학습(unsupervised learning) 또는 자기 지도 학습(self-supervised learning)을 사용하여 학습됩니다.** 다시 말해서, 레이블이 지정되지 않은 원시 멀티모달 데이터에 대해 학습되며, 학습 과정에서 사람이 주석을 달거나 데이터에 레이블을 지정할 필요가 없습니다.

- 수십억 개의 파라미터로 학습된 매우 심층적인 신경망을 기반으로 하는 **상당히 큰 모델입니다.**

- **일반적으로 다른 모델의 '기초(foundation)' 역할을 하도록 만들어졌기 때문에** 다른 모델을 구축하기 위한 출발점으로 사용할 수 있으며, 미세 조정을 통해 이를 수행할 수 있습니다.

![Foundation Models versus LLMs](../../images/FoundationModel.png?WT.mc_id=academic-105485-koreyst)

Image source: [Essential Guide to Foundation Models and Large Language Models | by Babar M Bhatti | Medium
](https://thebabar.medium.com/essential-guide-to-foundation-models-and-large-language-models-27dab58f7404)

이 구분을 더 명확히 하기 위해 ChatGPT를 예로 들어보겠습니다. ChatGPT의 첫 번째 버전을 구축하기 위해 GPT-3.5라는 모델이 파운데이션 모델로 사용되었습니다. 즉, OpenAI는 일부 채팅 관련 데이터를 사용하여 챗봇과 같은 대화형 시나리오에서 잘 작동하도록 특화된 GPT-3.5의 튜닝된 버전을 만들었습니다.

![Foundation Model](../../images/Multimodal.png?WT.mc_id=academic-105485-koreyst)

Image source: [2108.07258.pdf (arxiv.org)](https://arxiv.org/pdf/2108.07258.pdf?WT.mc_id=academic-105485-koreyst)

### 오픈 소스 모델 vs. 독점 상용 모델(Proprietary Models)

LLM을 분류하는 또 다른 방법은 오픈 소스인지 독점적인지 여부입니다.

오픈 소스 모델은 대중에게 공개되어 누구나 사용할 수 있는 모델입니다. 오픈 소스 모델은 모델을 만든 회사나 연구 커뮤니티에서 제공하는 경우가 많습니다. 이러한 모델은 LLM의 다양한 사용 사례에 맞게 검사, 수정 및 커스터마이징될 수 있습니다. 그러나 이러한 모델이 항상 프로덕션 사용에 최적화되어 있는 것은 아니며 독점 모델만큼 성능이 뛰어나지 않을 수 있습니다. 또한 오픈 소스 모델에 대한 자금 지원이 제한될 수 있으며, 장기적으로 유지 관리되지 않거나 최신 연구로 업데이트되지 않을 수 있습니다. 인기 있는 오픈 소스 모델의 예로는 [Alpaca](https://crfm.stanford.edu/2023/03/13/alpaca.html?WT.mc_id=academic-105485-koreyst), [Bloom](https://sapling.ai/llm/bloom?WT.mc_id=academic-105485-koreyst) 그리고 [LLaMA](https://sapling.ai/llm/llama?WT.mc_id=academic-105485-koreyst) 등이 있습니다.

독점 모델은 회사에서 소유하고 대중에게 공개하지 않는 모델입니다. 이러한 모델은 종종 프로덕션용으로 최적화되어 있습니다. 그러나 이러한 모델은 다른 사용 사례에 맞게 검사, 수정 또는 커스터마이징될 수 없습니다. 또한 항상 무료로 제공되는 것은 아니며 사용하려면 구독 또는 결제가 필요할 수 있습니다. 또한 사용자는 모델 학습에 사용되는 데이터를 제어할 수 없으므로 모델 소유자에게 데이터 프라이버시 및 책임감 있는 AI 사용에 대한 약속을 맡겨야 합니다. 널리 사용되는 독점 모델의 예로는[OpenAI models](https://platform.openai.com/docs/models/overview?WT.mc_id=academic-105485-koreyst), [Google Bard](https://sapling.ai/llm/bard?WT.mc_id=academic-105485-koreyst) 또는 [Claude 2](https://www.anthropic.com/index/claude-2?WT.mc_id=academic-105485-koreyst)가 있습니다.

### 임베딩(Embedding) vs. 이미지 생성(Image generation) vs. 텍스트 및 코드 생성(Text and Code generation)

LLM은 생성하는 출력의 종류에 따라 분류할 수도 있습니다.

Embeddings은 텍스트를 숫자 형태로 변환할 수 있는 모델류의 집합이며, 입력 텍스트를 숫자 형태로 표현하는 것을 임베딩(embedding)이라고 합니다. 임베딩을 사용하면 기계가 단어나 문장 간의 관계를 더 쉽게 이해할 수 있으며, 수치 데이터에서 더 나은 성능을 발휘하는 분류 모델이나 클러스터링 모델과 같은 다른 모델의 입력으로 사용할 수 있습니다. 임베딩 모델은 데이터가 풍부한 분야의 특정 작업을 위해 일단 모델을 구축한 다음, 모델 가중치(임베딩)를 다른 다운스트림 작업에 재사용하는 전이 학습(transfer learning)에 자주 사용됩니다. 이러한 방식의 예로는 [OpenAI embeddings](https://platform.openai.com/docs/models/embeddings?WT.mc_id=academic-105485-koreyst)이 있습니다.

![Embedding](../../images/Embedding.png?WT.mc_id=academic-105485-koreyst)

이미지 생성 모델(image generation models)은 말 그대로 이미지를 생성하는 모델입니다. 이러한 모델은 이미지 편집, 이미지 합성 및 이미지 번역에 자주 사용됩니다. 이미지 생성 모델은 종종 [LAION-5B](https://laion.ai/blog/laion-5b/?WT.mc_id=academic-105485-koreyst)와 같은 대규모 이미지 데이터 세트에 대해 학습되며, 새로운 이미지를 생성하거나 인페인팅, 초고해상도 및 색상화 기술을 사용하여 기존 이미지를 편집하는 데 사용할 수 있습니다. 예를 들어 [DALL-E-3](https://openai.com/dall-e-3?WT.mc_id=academic-105485-koreyst) 및 [Stable Diffusion](https://github.com/Stability-AI/StableDiffusion?WT.mc_id=academic-105485-koreyst) 모델 등이 있습니다.

![Image generation](../../images/Image.png?WT.mc_id=academic-105485-koreyst)

텍스트 및 코드 생성 모델(text and code generation models)은 텍스트 또는 코드를 생성하는 모델입니다. 이러한 모델은 텍스트 요약, 번역 및 질의응답(Question Answering)에 자주 사용됩니다. 텍스트 생성 모델은 [BookCorpus](https://www.cv-foundation.org/openaccess/content_iccv_2015/html/Zhu_Aligning_Books_and_ICCV_2015_paper.html?WT.mc_id=academic-105485-koreyst)와 같은 대규모 텍스트 데이터 세트에 대해 학습되는 경우가 많으며, 새로운 텍스트를 생성하거나 질문에 답변하는 데 사용할 수 있습니다. [CodeParrot](https://huggingface.co/codeparrot?WT.mc_id=academic-105485-koreyst)과 같은 코드 생성 모델은 종종 GitHub와 같은 대규모 코드 데이터 세트에 대해 학습되며 새 코드를 생성하거나 기존 코드의 버그를 수정하는 데 사용할 수 있습니다.

 ![Text and code generation](../../images/Text.png?WT.mc_id=academic-105485-koreyst)

### 인코더-디코더(Encoder-Decoder) vs. 디코더 전용(Decoder-only) 모델

LLM의 다양한 아키텍처 유형에 대해 이야기하기 위해 비유를 들어보겠습니다.

관리자가 학생들을 위한 퀴즈를 작성하라는 과제를 주었다고 가정해 보겠습니다. 한 명은 콘텐츠 작성 작업을 감독하고 다른 한 명은 검토 작업을 감독하는 두 명의 동료가 있습니다.

콘텐츠 작성자는 디코더 전용 모델(Decoder-only models)과 같아서 주제를 보고 이미 작성된 내용을 확인한 다음 이를 기반으로 계속해서 내용을 작성할 수 있습니다. 이들은 흥미롭고 유익한 콘텐츠를 작성하는 데는 매우 능숙하지만 주제와 학습 목표를 이해하는 데는 능숙하지 않습니다. 디코더 모델의 몇 가지 예로는 GPT-3과 같은 GPT 제품군 모델이 있습니다.

검토자는 인코더 전용 모델(Encoder-only models)과 비슷하며, 작성된 퀴즈와 답안을 보고 그들 간의 관계를 파악하고 문맥을 이해하지만 콘텐츠를 생성하는 데는 능숙하지 않습니다. 인코더 전용 모델의 예로는 BERT가 있습니다.

퀴즈를 만들고 검토할 수 있는 사람이 있다고 상상해 보세요. 이것이 바로 인코더-디코더(encoder-decoder) 모델입니다. 몇 가지 예로 BART와 T5를 들 수 있습니다.

### 서비스와 모델

이제 서비스와 모델의 차이점에 대해 이야기해 보겠습니다. 서비스는 클라우드 서비스 제공업체(Cloud Service Provider)에서 제공하는 상품으로, 모델, 데이터 및 기타 구성 요소가 결합된 경우가 많습니다. 모델은 서비스의 핵심 구성 요소이며, 종종 LLM과 같은 기초 모델입니다.

서비스는 종종 상용화에 최적화되어 있으며 그래픽 사용자 인터페이스를 통해 모델보다 사용하기 쉬운 경우가 많습니다. 그러나 서비스가 항상 무료로 제공되는 것은 아니며, 서비스 소유자의 장비와 리소스를 활용하고 비용을 최적화하며 쉽게 확장하는 대신 구독 또는 지불을 통해서만 사용할 수 있습니다. 예를 들어 종량제 요금제를 제공하는 [Azure OpenAI service](https://learn.microsoft.com/azure/ai-services/openai/overview?WT.mc_id=academic-105485-koreyst) 서비스는 사용자가 서비스를 사용한 양에 비례하여 요금이 부과됩니다. 또한 Azure OpenAI 서비스는 모델의 기능에 엔터프라이즈급 보안과 Responsible AI 프레임워크를 제공합니다.

모델은 매개변수, 가중치 등이 포함된 신경망에 불과합니다. 그러나 기업이 로컬에서 실행하려면 장비를 구입하고, 확장할 수 있는 구조를 구축해야 하며, 라이선스를 구매하거나 오픈 소스 모델을 사용해야 합니다. LLaMA와 같은 모델을 사용할 수 있지만, 모델을 실행하기 위한 연산 능력(computation power)이 필요합니다.

## 다양한 모델을 반복적으로 테스트해서 Azure의 성능을 파악하는 방법

우리 스타트업 팀이 현재 LLM 환경(LLM landscape)를 탐색하고 시나리오에 적합한 몇 가지 후보를 파악했다면 다음 단계는 팀이 보유한 데이터와 작업량(workload)을 바탕으로 이를 테스트하는 것입니다. 이 과정은 실험과 측정을 통해 반복적으로 수행됩니다. 이전 단락에서 언급한 대부분의 모델(OpenAI 모델, Llama2와 같은 오픈 소스 모델, Hugging Face Transformers)은 [Azure Machine Learning studio](https://ml.azure.com/?WT.mc_id=academic-105485-koreyst)의 [Foundation Models](https://learn.microsoft.com/azure/machine-learning/concept-foundation-models?WT.mc_id=academic-105485-koreyst) 카탈로그에서 사용할 수 있습니다.

[Azure Machine Learning](https://azure.microsoft.com/products/machine-learning/?WT.mc_id=academic-105485-koreyst)은 데이터 과학자와 ML 엔지니어가 단일 플랫폼에서 전체 ML 수명 주기(교육, 테스트, 배포 및 MLOps 처리)를 관리할 수 있도록 설계된 클라우드 서비스입니다. 

Azure Machine Learning studio는 이 서비스에 그래픽 사용자 인터페이스를 제공하며 사용자가 다음을 수행할 수 있도록 합니다:

- 작업, 라이선스 또는 이름별로 필터링하여 카탈로그에서 관심 있는 파운데이션 모델을 찾을 수 있습니다. 카탈로그에 아직 포함되지 않은 새 모델을 가져올 수도 있습니다.

- 자세한 설명과 코드 샘플이 포함된 모델 카드를 검토하고 샘플 추론 위젯을 사용하여 결과를 테스트할 수 있는 샘플 프롬프트를 제공하여 테스트할 수 있습니다.

![Model card](../../images/Llama1.png?WT.mc_id=academic-105485-koreyst)

- 특정 워크로드 및 입력으로 제공된 데이터 세트에 대한 객관적인 평가 메트릭을 사용하여 모델 성능을 평가할 수 있습니다.

![Model evaluation](../../images/Llama2.png?WT.mc_id=academic-105485-koreyst)

- Azure Machine Learning의 실험 및 추적 기능을 활용하여 특정 워크로드에서 모델 성능을 개선하기 위해 사용자 지정 학습 데이터에서 모델을 미세 조정(fine-tune)할 수 있습니다.

![Model fine-tuning](../../images/Llama3.png?WT.mc_id=academic-105485-koreyst)

- 사전 학습된 원본 모델 또는 미세 조정된 버전을 원격 실시간 추론 또는 일괄 처리 엔드포인트에 배포하여 애플리케이션에서 사용할 수 있도록 할 수 있습니다.

![Model deployment](../../images/Llama4.png?WT.mc_id=academic-105485-koreyst)

## LLM 결과의 개선

우리 스타트업 팀과 함께 다양한 종류의 LLM과 클라우드 플랫폼(Azure 머신 러닝)을 탐색하여 모델을 비교하고, 테스트 데이터로 평가하고, 성능을 개선하고, 추론 엔드포인트에 배포할 수 있었습니다.

하지만 언제 사전 학습 모델을 그대로 사용하는 대신 모델을 미세 조정하는 것을 고려해야 할까요? 특정 워크로드에서 모델 성능을 개선할 수 있는 다른 접근 방식이 있을까요?

비즈니스가 LLM에서 필요한 결과를 얻기 위해 사용할 수 있는 몇 가지 접근 방식이 있으며, 다양한 수준의 학습을 통해 다양한 유형의 모델을 선택할 수 있습니다.

복잡성, 비용 및 품질 수준이 다른 프로덕션 환경에 LLM을 배포할 수 있습니다. 다음은 몇 가지 접근 방식입니다:

- **Prompt engineering with context**. LLM에 프롬프트(prompt)를 보낼 때 충분한 컨텍스트를 제공하여 필요한 응답을 얻을 수 있도록 하자는 취지입니다.

- **Retrieval Augmented Generation, RAG**. 예를 들어, 데이터베이스나 웹 엔드포인트에 데이터가 있을 수 있는데, 이 데이터 또는 데이터의 일부가 프롬프트(prompt)에 포함되도록 하려면 관련 데이터를 가져와서 해당 부분을 사용자 프롬프트의 일부로 만들면 됩니다.

- **Fine-tuned model**. 여기에서는 자체 데이터에 대해 모델을 추가로 학습시켜 모델을 더 정확하고 필요에 맞게 응답할 수 있도록 하지만 비용이 많이 들 수 있습니다.

![LLMs deployment](../../images/Deploy.png?WT.mc_id=academic-105485-koreyst)

Img source: [Four Ways that Enterprises Deploy LLMs | Fiddler AI Blog](https://www.fiddler.ai/blog/four-ways-that-enterprises-deploy-llms?WT.mc_id=academic-105485-koreyst)

### Prompt Engineering with Context

사전 학습된 LLM은 완성해야 할 문장이나 질문과 같은 짧은 프롬프트만 호출해도 일반화된 자연어 작업을 매우 잘 수행하며, 이른바 '제로 샷(zero-shot)' 학습을 통해 학습할 수 있습니다.

그러나 사용자가 자세한 요청과 예시, 즉 컨텍스트를 통해 질의를 구성할수록 더 정확하고 사용자의 기대에 가장 근접한 답변을 얻을 수 있습니다. 이 경우 프롬프트에 예시가 하나만 포함되어 있으면 '원샷(one-shot)' 학습, 여러 예시가 포함되어 있으면 '퓨샷(few-shot) 학습'이라고 합니다.
컨텍스트가 포함된 프롬프트 엔지니어링은 시작하기에 가장 비용 효율적인 접근 방식입니다.

### Retrieval Augmented Generation (RAG)

LLM은 학습에 사용된 데이터에만 기반하여 답변을 생성할 수 있다는 한계가 있습니다. 즉, 학습 과정 이후에 발생한 사실에 대해서는 전혀 알지 못하며 회사 데이터와 같은 비공개 정보에 액세스할 수 없습니다.

이 문제는 프롬프트 길이 제한을 고려하여 문서 청크 형태의 외부 데이터로 프롬프트를 보강하는 기술인 RAG를 통해 극복할 수 있습니다. 이는 미리 정의된 다양한 데이터 소스에서 유용한 청크를 검색하여 프롬프트 컨텍스트에 추가하는 벡터 데이터베이스 도구(예: [Azure Vector Search](https://learn.microsoft.com/azure/search/vector-search-overview?WT.mc_id=academic-105485-koreyst))를 통해 지원됩니다.

이 기법은 기업이 LLM을 미세 조정할 데이터, 시간 또는 리소스가 충분하지 않지만 특정 워크로드에서 성능을 개선하고 현실을 왜곡하거나 유해한 콘텐츠와 같은 조작의 위험을 줄이려는 경우에 매우 유용합니다.

### Fine-tuned model

미세 조정은 전이 학습을 활용하여 모델을 다운스트림 작업에 '적응'시키거나 특정 문제를 해결하기 위한 프로세스입니다. 단발성 학습 및 RAG와는 달리, 가중치와 편향이 업데이트된 새로운 모델이 생성됩니다. 이를 위해서는 단일 입력(the prompt)과 관련 출력(the completion)으로 구성된 훈련 예제 세트가 필요합니다. 다음과 같은 경우 선호되는 접근 방식입니다:

- **미세 조정된 모델 사용**. 기업에서 고성능 모델보다는 임베딩 모델과 같이 성능이 낮은 모델을 미세 조정하여 보다 비용 효율적이고 빠른 솔루션을 사용하고자 하는 경우.

- **지연 시간 고려**. 특정 사용 사례에서는 지연 시간(latency)이 중요하므로 매우 긴 프롬프트를 사용할 수 없거나 모델에서 학습해야 하는 예제 수가 프롬프트 길이 제한에 맞지 않는 경우가 있습니다.

- **최신 상태 유지**. 비즈니스에는 많은 고품질 데이터와 실측 데이터 레이블이 있으며, 시간이 지남에 따라 이 데이터를 최신 상태로 유지하는 데 필요한 리소스가 있습니다.

### 학습된 모델

LLM을 처음부터 학습시키는 것은 의심할 여지 없이 가장 어렵고 복잡한 접근 방식이며, 방대한 양의 데이터, 숙련된 리소스, 적절한 컴퓨팅 파워가 필요합니다. 이 옵션은 비즈니스에 도메인별 사용 사례와 대량의 도메인 중심 데이터가 있는 시나리오에서만 고려해야 합니다.

## Knowledge check

LLM 응답 결과를 개선하기 위한 좋은 접근 방식은 무엇일까요?

1. 컨텍스트를 고려한 신속한 엔지니어링
1. RAG
1. 미세 조정된 모델

A:3, 시간과 리소스가 충분하고 고품질 데이터가 있다면 미세 조정이 최신 상태를 유지하는 데 더 나은 옵션입니다. 하지만 개선할 사항이 많은데 시간이 부족하다면 RAG를 먼저 고려하는 것이 좋습니다.

## 🚀 Challenge

비즈니스에 [RAG를 사용](https://learn.microsoft.com/azure/search/retrieval-augmented-generation-overview?WT.mc_id=academic-105485-koreyst)하는 방법에 대해 자세히 알아보세요.

## 잘 하셨습니다. 계속 학습하세요.

이 강좌를 완료한 후에는 [생성형 AI 학습 컬렉션](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst)을 확인하여 생성형 AI 지식의 수준을 계속 높여보세요!

3강에서 [책임감 있게 생성형 AI로 빌드](../../../03-using-generative-ai-responsibly/README.md?WT.mc_id=academic-105485-koreyst)하는 방법을 살펴보세요!