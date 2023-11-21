# 강좌 시작하기

본 강좌를 학습함으로써 생성형 AI (Generative AI)로 무엇을 만들 수 있을지 영감을 얻으실 수 있기를 기대합니다!

본 과정을 성공으로 완료할 수 있도록 설정 단계, 기술 요구 사항, 필요할 때 도움을 받는 방법을 간략하게 설명하는 본 페이지를 만들었습니다.

## 설정 단계

이 강좌를 수강하려면 다음 단계를 완료해야 합니다.

### 1. 이 리포지토리를 Fork 하기

[전체 리포지토리](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst)를 자신의 GitHub 계정으로 포크하여 코드를 변경하고 챌린지를 완료할 수 있습니다. [이 리포지토리](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst)에 별표(🌟)를 표시하여 이 리포지토리와 관련 리포지토리를 더 쉽게 찾을 수도 있습니다.

### 2. 코드스페이스(codespace) 생성

코드를 실행할 때 종속성 문제를 방지하려면 이 과정을 GitHub 코드스페이스에서 실행하는 것이 좋습니다.

이 리포지토리의 fork된 버전에서 `Code` 옵션을 선택하고 **Codespaces** 옵션을 선택하면 만들 수 있습니다.

### 3. 본인의 API 키 저장하기

모든 유형의 애플리케이션을 구축할 때는 API 키를 안전하게 보관하는 것이 중요합니다. 이러한 세부 정보를 공개 리포지토리에 커밋하면 원치 않는 비용과 문제가 발생할 수 있으므로 작업 중인 코드에 API 키를 직접 저장하지 않는 것이 좋습니다.

![코드스페이스를 생성하는 버튼을 표시하는 대화 상자](../../images/who-will-pay.webp?WT.mc_id=academic-105485-koreyst)

## 본인 컴퓨터에서 로컬로 실행하는 방법

컴퓨터에서 로컬로 코드를 실행하려면 특정 버전의 [Python이 설치](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst)되어 있어야 합니다.

그런 다음 리포지토리를 사용하려면 해당 리포지토리를 복제해야 합니다:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

이제 모든 것이 준비되었으므로 코드를 가지고 학습하고 실행할 수 있습니다.

### Miniconda 설치(선택 사항)

**[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst)** 설치를 통해서 서로 다른 다중 Python **가상환경(Virtural environment)** 관리를 위한 경량의 `conda` 패키지 관리자를 활용할 수 있습니다. `conda`를 사용하면 다양한 파이썬 버전과 패키지를 쉽게 설치하고 전환할 수 있으며 `pip`를 통해 사용할 수 없는 패키지도 설치할 수 있습니다.

Miniconda를 설치한 후에는 리포지토리를 복제하고(아직 복제하지 않은 경우) 이 코스에 사용할 가상 환경을 생성해야 합니다:

아래 단계를 실행하기 전에 먼저 *environment.yml* 파일이 있는지 확인하세요. *environment.yml* 파일은 필요한 종속성이 있는 `conda` 환경을 생성하는 데 사용되며 다음과 같은 내용을 포함하고 있습니다:

```yml
name: <environment-name>
channels:  
 - defaults
dependencies:  
- python=<python-version>  
- openai  
- python-dotenv
```

`<environment-name>`은 `conda` 환경의 이름으로, `<python-version>`은 사용하려는 Python 버전으로 대체할 수 있습니다. 생성한 *environment.yml* 파일을 리포지토리의 *.devcontainer* 폴더에 넣습니다.

*environment.yml* 파일을 만들었으면 이제 다음 명령으로 콘다(conda) 환경을 만들 수 있습니다:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml
conda activate ai4beg
```

문제가 발생하면 콘다(conda) 환경 만들기에 대한 이 [링크](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst)를 참조하세요.

### Visual Studio Code (w/ Python Extension) 사용

아마도 본 강좌를 가장 잘 활용하는 방법은 [Python Extention](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst)이 포함된 [Visual Studio Code](http://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst)를 사용하는 것입니다.

> **주의사항**: VS Code에서 디렉터리를 복제하고 열면 자동으로 Python 확장 프로그램을 설치하도록 제안합니다. 또한 위에서 설명한 대로 miniconda를 설치해야 합니다.

> **주의사항**: VS Code의 컨테이너에서 리포지토리를 다시 열 것을 제안하는 경우, 이를 거부해야 로컬 Python 설치를 사용할 수 있습니다.

### 브라우저에서 Jupyter 사용

내 컴퓨터의 브라우저에서 바로 Jupyter 환경을 사용할 수도 있습니다. 실제로 클래식 Jupyter와 Jupyer Hub 모두 자동 완성, 코드 하이라이팅 등 상당히 편리한 개발 환경을 제공합니다.

로컬에서 Jupyter를 시작하려면 코스의 디렉토리로 이동하여 실행하면 됩니다:

```bash
jupyter notebook
```

혹은

```bash
jupyterhub
```

그런 다음 원하는 `.ipynb` 파일을 열고 작업을 시작할 수 있습니다.

### 컨테이너에서 실행

파이썬 설치의 대안은 컨테이너에서 코드를 실행하는 것입니다. 본 리포지토리에는 리포지토리에 컨테이너를 빌드하는 방법을 알려주는 특수한 `.devcontainer` 폴더가 있으므로, VS Code는 컨테이너에서 코드를 다시 열도록 제안할 것입니다. 이 경우 Docker 설치가 필요하고 더 복잡해지므로 숙련된 사용자에게만 권장합니다.

GitHub Codespaces를 사용할 때 API 키를 안전하게 유지하는 가장 좋은 방법 중 하나는 Codespace Secrets을 사용하는 것입니다. Codespace의 Secrets을 관리하는 방법은 [본 가이드](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst)를 참조하세요.

## 본 강좌에서 제공되는 수업과 기술적 요구 사항

이 과정은 6개의 개념 수업과 6개의 코딩 수업으로 구성되어 있습니다.

코딩 수업에서는 Azure OpenAI 서비스를 사용합니다. 이 코드를 실행하려면 Azure OpenAI 서비스에 대한 액세스 권한과 API 키가 필요합니다. [신청서](https://customervoice.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR7en2Ais5pxKtso_Pz4b1_xUOFA5Qk1UWDRBMjg0WFhPMkIzTzhKQ1dWNyQlQCN0PWcu&culture=en-us&country=us&WT.mc_id=academic-105485-koreyst)를 작성하여 액세스 권한을 신청할 수 있습니다.

신청서가 처리될 때까지 기다리는 동안 각 코딩 수업에는 코드와 출력을 볼 수 있는 `README.md` 파일도 포함되어 있습니다.

## 처음으로 Azure OpenAI 서비스 사용

Azure OpenAI 서비스를 처음 사용하는 경우 [이 가이드](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)에서 Azure OpenAI 서비스 리소스를 만들고 배포하는 방법을 참조하세요.

## 다른 학습자 만나기

우리는 공식 [AI 커뮤니티 디스코드 서버](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)에 다른 학습자들과 만날 수 있는 채널을 만들었습니다. 같은 생각을 가진 다른 기업가, 빌더, 학생, 그리고 생성형 AI 지식 수준을 높이려는 모든 사람과 네트워크를 형성할 수 있는 좋은 방법입니다.

[![Join discord channel](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

프로젝트 팀도 이 Discord 서버에서 모든 학습자를 도울 것입니다.

## 기여(Contribution)

이 과정은 오픈소스 이니셔티브입니다. 개선할 부분이나 문제가 발견되면 [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst)를 만들거나 [Github issue](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst)를 기록해 주세요.

프로젝트 팀에서 모든 기여를 추적할 것이며, 오픈소스에 기여하는 것은 생성형 AI 분야에서 경력을 쌓을 수 있는 훌륭한 방법입니다.

기여를 제공하려면 대부분 기여자 라이선스 계약(CLA)에 동의해야 하며, 이를 통해 기여 내용을 사용할 수 있는 권리를 우리에게 부여할 수 있음을 선언합니다. 자세한 내용은 [CLA, 기여자 라이선스 계약](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst) 웹사이트를 참조하세요.

중요: 이 리포지토리에 있는 텍스트를 번역할 때는 기계 번역을 사용하지 마십시오. 커뮤니티를 통해 번역을 검증할 예정이므로 자신이 능숙한 언어로만 번역에 자원해 주세요.

Pull Request를 제출하면 CLA 봇이 자동으로 CLA 제공 여부를 결정하고 PR을 적절하게 꾸밉니다(예: 레이블, 댓글). 봇이 제공하는 지침을 따르기만 하면 됩니다. CLA를 사용하는 모든 리포지토리에 대해 이 작업을 한 번만 수행하면 됩니다.

이 프로젝트는 Microsoft 오픈 소스 행동 강령을 채택했습니다. 자세한 내용은 행동 강령 FAQ를 참조하거나 추가 질문이나 의견이 있는 경우 [오픈코드](opencode@microsoft.com)에 이메일로 문의하세요.

## 자 이제 시작해 봅시다

이제 이 과정을 성공적으로 이수하는 데 필요한 단계를 완료했으므로 이제 [생성형 AI와 LLM의 개요](../../../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst)로 시작해 보겠습니다.