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

