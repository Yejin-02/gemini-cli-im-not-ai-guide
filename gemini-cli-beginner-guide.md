# Gemini CLI에 im-not-ai 설치하고 사용하는 법

이 문서는 Gemini 웹사이트만 사용해 보았고, 터미널이나 개발 도구가 익숙하지 않은 분을 위한 안내서입니다.

이 안내서의 마지막 단계까지 완료하면 터미널에서 Gemini를 실행한 뒤 다음처럼 한글 글을 윤문할 수 있습니다.

~~~text
/humanize-korean
~~~

## 먼저 알아둘 점

**im-not-ai는 Gemini 웹사이트에 설치하는 브라우저 확장 프로그램이 아닙니다. Google의 Gemini CLI라는 터미널용 프로그램에 설치하는 확장 기능입니다.**

**따라서 순서는 다음과 같습니다.**

1. Node.js 설치
2. Gemini CLI 설치
3. Gemini CLI에서 Google 계정 로그인
4. im-not-ai 확장 기능 설치
5. Gemini CLI에서 im-not-ai 사용

처음에는 터미널이라는 낯선 화면을 사용하지만, **명령어를 한 줄씩 복사해서 붙여넣는 방식으로 진행합니다. 프로그래밍을 배울 필요는 없습니다.**

이 문서는 개인 Google 계정으로 로그인하는 가장 간단한 경로를 기준으로 작성했습니다. 회사·학교 계정은 Google Cloud 프로젝트를 추가로 요구할 수 있습니다.

## 준비물

- 인터넷에 연결된 macOS 컴퓨터
- 로그인할 Google 계정
- 약 15~30분
- 글을 복사하고 붙여넣을 수 있는 정도의 컴퓨터 사용 경험

**회사 문서, 개인정보, 공개되면 안 되는 원고를 테스트할 때는 주의하세요.** 이 도구를 사용하는 글은 Google의 Gemini 서비스로 전송됩니다.

## 명령어를 입력하는 방법

이 안내서에는 다음처럼 회색 상자 안에 명령어가 나옵니다.

~~~bash
node --version
~~~

**명령어를 입력할 때는 다음처럼 하세요.**

1. 회색 상자 안의 한 줄을 복사합니다.
2. 터미널 창을 클릭합니다.
3. 붙여넣습니다.
4. Enter 키를 누릅니다.
5. 화면에 출력이 나타날 때까지 기다립니다.

**상자 안의 달러 기호나 꺾쇠 기호는 입력하지 않습니다.** 상자 안의 명령어만 그대로 복사하면 됩니다.

**명령어가 실행되는 동안에는 같은 명령어를 여러 번 누르지 마세요.** 몇 초에서 몇 분이 걸릴 수 있습니다.

---

## 1. Node.js 설치하기

**Node.js는 Gemini CLI가 실행되는 데 필요한 바탕 프로그램입니다.** Gemini 자체를 설치하는 것은 아니며, Gemini CLI가 작동할 수 있게 해 주는 실행 환경입니다.

### 1-1. macOS인 경우

#### 터미널 열기

1. 키보드에서 Command(⌘) + Space를 누릅니다.
2. 터미널 또는 Terminal을 검색합니다.
3. Enter를 누릅니다.

검은색 또는 흰색 창이 하나 열리면 터미널입니다. 창 안에 다음과 비슷한 글자가 보일 수 있습니다.

~~~text
Last login: ...
your-name@your-mac ~ %
~~~

이 화면이 보이면 정상입니다. 뒤에 있는 퍼센트 기호는 명령어를 입력하라는 표시이지, 직접 입력하는 글자가 아닙니다.

#### Node.js 내려받기

1. 웹 브라우저에서 [Node.js 공식 다운로드 페이지](https://nodejs.org/en/download/)를 엽니다.
2. LTS라고 표시된 버전을 선택합니다.
3. macOS용 설치 파일인 pkg 파일을 내려받습니다.
4. 내려받은 파일을 엽니다.
5. 설치 화면에서 Continue를 여러 번 누릅니다.
6. 사용권에 동의하고 Install을 누릅니다.
7. Mac 로그인 암호를 요구하면 입력합니다.
8. 설치가 완료되면 Close를 누릅니다.

**Current가 아니라 LTS를 선택하세요.** LTS가 일반 사용자에게 안정적인 장기 지원 버전이기 때문입니다.

#### 설치 확인

**Node.js 설치 후에는 터미널을 완전히 닫았다가 새로 여는 것이 좋습니다.** 그다음 다음 명령어를 차례대로 입력합니다.

~~~bash
node --version
~~~

정상적인 출력 예시는 다음과 같습니다.

~~~text
v22.14.0
~~~

**숫자는 달라도 괜찮습니다. v20 이상이면 됩니다.**

이번에는 다음 명령어를 입력합니다.

~~~bash
npm --version
~~~

정상적인 출력 예시는 다음과 같습니다.

~~~text
10.9.2
~~~

**숫자가 보이면 Node.js 설치가 끝난 것입니다.** npm은 Node.js 프로그램을 설치할 때 사용하는 도구입니다.

### 1-3. Node.js 설치 단계에서 자주 생기는 문제

#### node를 찾을 수 없다는 메시지가 나오는 경우

macOS에서는 다음과 비슷한 메시지가 나올 수 있습니다.

~~~text
zsh: command not found: node
~~~

다음 순서로 다시 확인하세요.

1. Node.js 설치 파일을 실제로 실행했는지 확인합니다.
2. 설치가 끝났다면 터미널을 완전히 닫습니다.
3. 터미널을 새로 엽니다.
4. node --version을 다시 입력합니다.

그래도 같은 메시지가 나오면 Node.js 설치 화면을 끝까지 진행했는지 확인하고 다시 설치합니다.

#### npm만 찾을 수 없는 경우

Node.js 설치가 중간에 끝났거나, 터미널이 이전 환경을 사용하고 있을 가능성이 큽니다. 터미널을 닫고 다시 연 다음 다음 두 명령어를 다시 확인하세요.

~~~bash
node --version
npm --version
~~~

---

## 2. Gemini CLI 설치하기

**이제 Node.js 위에 Gemini CLI를 설치합니다.**

### 2-1. 설치 명령어 입력

새 터미널 창에서 다음 명령어를 그대로 복사해 입력합니다.

~~~bash
npm install -g @google/gemini-cli
~~~

여기서 -g는 현재 컴퓨터에서 어느 폴더에 있든 gemini 명령어를 사용할 수 있도록 전역 설치한다는 뜻입니다. 이 설명을 외울 필요는 없습니다.

설치 중에는 다음처럼 여러 줄의 글자가 빠르게 지나갈 수 있습니다.

~~~text
added ... packages in ...s
~~~

또는 다음처럼 npm notice로 시작하는 안내가 나올 수 있습니다.

~~~text
npm notice New major version of npm available...
~~~

**npm notice는 보통 오류가 아니라 추가 안내입니다.** 마지막에 npm error가 없다면 일단 설치 확인을 진행하세요.

### 2-2. 설치 확인

다음 명령어를 입력합니다.

~~~bash
gemini --version
~~~

정상적인 출력은 다음과 비슷합니다.

~~~text
0.59.0
~~~

**버전 숫자는 달라도 됩니다. 숫자가 보이면 Gemini CLI가 설치된 것입니다.**

### 2-3. 설치 중 자주 생기는 문제

#### npm: command not found가 나오는 경우

1단계의 Node.js 설치가 제대로 끝나지 않은 것입니다. 먼저 다음을 확인합니다.

~~~bash
node --version
npm --version
~~~

둘 중 하나라도 찾을 수 없으면 Node.js 설치 단계로 돌아갑니다. Node.js를 설치한 뒤 터미널을 새로 열어야 합니다.

#### EACCES 또는 permission denied가 나오는 경우

macOS에서 다음과 비슷한 오류가 나올 수 있습니다.

~~~text
EACCES: permission denied
~~~

이 메시지는 전역 설치 위치에 쓸 권한이 없다는 뜻입니다. 같은 명령어를 계속 반복하지 말고 다음을 확인하세요.

1. Node.js를 공식 홈페이지의 LTS 설치 파일로 설치했는지 확인합니다.
2. 터미널을 닫았다가 새로 엽니다.
3. 같은 설치 명령어를 한 번만 다시 시도합니다.

그래도 계속 EACCES가 나오면 운영체제별 Node.js 설치 방식이 섞였을 가능성이 있습니다. 무작정 sudo를 붙이기보다 [Gemini CLI 공식 설치 문서](https://geminicli.com/docs/get-started/installation/)의 Homebrew 설치 방법을 사용하거나 컴퓨터에 익숙한 사람에게 도움을 받는 편이 안전합니다.

#### 인터넷 관련 오류가 나오는 경우

다음과 비슷한 메시지가 나오면 네트워크 문제일 수 있습니다.

~~~text
ETIMEDOUT
ENETUNREACH
network error
~~~

Wi-Fi 연결을 확인한 뒤 잠시 후 다음 명령어를 다시 시도하세요.

~~~bash
npm install -g @google/gemini-cli
~~~

회사나 학교 네트워크에서는 npm이 차단될 수 있습니다. 개인 네트워크에서 다시 시도해 보세요.

#### gemini를 찾을 수 없는 경우

설치가 끝났는데 다음처럼 나오는 경우입니다.

~~~text
zsh: command not found: gemini
~~~

먼저 터미널을 닫고 새로 연 다음 다시 확인하세요.

~~~bash
gemini --version
~~~

그래도 안 되면 설치 로그 마지막 부분에 오류가 있었는지 확인해야 합니다. npm install이 성공한 것처럼 보여도 npm error가 있었다면 성공한 것이 아닙니다.

---

## 3. Gemini CLI에서 Google 계정으로 로그인하기

### 3-1. Gemini CLI 실행

터미널에 다음을 입력합니다.

~~~bash
gemini
~~~

**처음 실행하면 화면이 바뀌면서 Gemini CLI의 대화형 화면이 열립니다.** 처음에는 글자가 많아 보여도 정상입니다.

처음 로그인하는 경우 다음과 비슷한 선택지가 나타납니다.

~~~text
How would you like to authenticate for this project?

1. Sign in with Google
2. Use Gemini API key
3. Use Vertex AI
~~~

**여기서는 1번인 Sign in with Google을 선택합니다.**

버전에 따라 숫자를 입력하거나, 위·아래 방향키로 선택한 뒤 Enter를 눌러야 할 수 있습니다.

### 3-2. 브라우저에서 로그인

Sign in with Google을 선택하면 보통 기본 웹 브라우저가 열립니다.

1. 로그인할 Google 계정을 선택합니다.
2. Gemini CLI가 Google 계정으로 로그인하는 것을 허용합니다.
3. 브라우저에 로그인 완료 화면이 나오면 브라우저 창을 닫거나 터미널로 돌아갑니다.

**개인 Gmail 계정은 대부분 Google Cloud 프로젝트를 따로 만들지 않아도 됩니다.** Google AI Pro나 Google AI Ultra를 사용 중이라면 해당 구독이 연결된 계정을 선택하세요.

**로그인이 끝나면 터미널에 다시 Gemini 대화 화면이 나타납니다.** 다음처럼 입력할 수 있는 줄이 보이면 성공입니다.

~~~text
>
~~~

꺾쇠 기호는 직접 입력할 필요가 없습니다. 그 뒤에 질문을 입력하면 됩니다.

### 3-3. 로그인 확인을 위한 간단한 테스트

다음처럼 짧은 문장을 입력해 보세요.

~~~text
안녕하세요. 한 문장으로 자기소개해 주세요.
~~~

정상이라면 잠시 후 Gemini의 답변이 터미널에 나타납니다.

내용이 정확히 같을 필요는 없습니다. 답변이 나오면 Gemini CLI가 로그인된 상태입니다.

### 3-4. 로그인 단계에서 자주 생기는 문제

#### 브라우저가 자동으로 열리지 않는 경우

터미널에 로그인 URL이 표시되거나, 브라우저에서 열 수 있는 주소가 표시되는지 확인하세요. 주소가 표시되면 그 주소를 복사해 브라우저 주소창에 붙여넣습니다.

아무 주소도 표시되지 않고 멈춘 것처럼 보이면 다음 순서로 시도하세요.

1. Enter를 한 번 눌러 봅니다.
2. 30초 정도 기다립니다.
3. 그래도 변화가 없으면 Ctrl+C를 눌러 현재 실행을 중단합니다.
4. 터미널을 새로 열고 gemini를 다시 실행합니다.

#### Google 계정을 선택했는데 다시 로그인 화면으로 돌아오는 경우

브라우저에서 팝업이나 새 창이 차단되었을 수 있습니다. 브라우저의 팝업 차단 알림을 확인하고 Gemini CLI 로그인 창을 허용한 뒤 다시 시도하세요.

#### 회사·학교 계정으로 Google Cloud 프로젝트를 요구하는 경우

회사, 학교, Google Workspace 계정은 개인 Gmail 계정과 달리 Google Cloud 프로젝트 설정이 필요할 수 있습니다. 이 안내서는 개인 계정 기준이므로, 가장 간단한 테스트는 개인 Google 계정으로 로그인하는 것입니다.

#### API 키를 입력하라고 하는 경우

**이 안내서의 기본 경로는 API 키가 아니라 Sign in with Google입니다.** 선택 화면에서 Sign in with Google을 선택하세요.

API 키를 다른 사람에게 보내거나 화면 캡처로 공유하지 마세요.

---

## 4. im-not-ai 설치하기

Gemini CLI에 로그인한 뒤, 이제 한글 윤문 기능을 추가합니다.

### 4-1. Gemini 대화 화면에서 나오기

**im-not-ai 설치 명령어는 Gemini 대화 화면이 아니라 일반 터미널 명령어로 입력해야 합니다.**

다음 중 하나를 사용하세요.

- Gemini 화면에서 /quit를 입력하고 Enter를 누릅니다.
- 또는 Ctrl+C를 한 번 눌러 Gemini를 종료합니다.
- 또는 새 터미널 창을 하나 더 엽니다.

새 터미널 창을 여는 방법은 다음과 같습니다.

- macOS: Command(⌘) + Space → 터미널 검색 → 새로 열기

### 4-2. 확장 기능 설치 명령어 입력

일반 터미널에서 다음 명령어를 그대로 입력합니다.

~~~bash
gemini extensions install https://github.com/epoko77-ai/im-not-ai.git
~~~

잠시 기다리면 GitHub에서 확장 기능을 내려받고 설치합니다. 성공 메시지의 문구는 Gemini CLI 버전에 따라 조금 다를 수 있지만, 보통 im-not-ai라는 이름과 설치 완료를 나타내는 문구가 포함됩니다.

**이 명령어는 이 레포를 컴퓨터에 직접 개발용으로 복제하는 과정이 아닙니다.** Gemini CLI가 사용할 수 있도록 확장 기능으로 등록하는 과정입니다.

### 4-3. 설치 확인

다음 명령어를 입력합니다.

~~~bash
gemini extensions list
~~~

목록에 다음과 비슷한 항목이 보이면 성공입니다.

~~~text
im-not-ai
~~~

**표시되는 버전이나 상세 상태는 달라도 됩니다. 핵심은 im-not-ai가 목록에 있고 오류가 없는 것입니다.**

Gemini 대화 화면 안에서도 다음 명령어로 확인할 수 있습니다.

~~~text
/extensions list
~~~

### 4-4. 설치 단계에서 자주 생기는 문제

#### gemini extensions를 알 수 없다는 메시지가 나오는 경우

Gemini CLI가 너무 오래된 버전일 수 있습니다. 먼저 버전을 확인합니다.

~~~bash
gemini --version
~~~

그다음 최신 안정 버전으로 업데이트합니다.

~~~bash
npm install -g @google/gemini-cli@latest
~~~

터미널을 닫았다가 다시 열고 확장 기능 설치 명령어를 다시 입력합니다.

#### 이미 설치되어 있다고 나오는 경우

이미 설치된 상태일 수 있습니다. 다음 명령어로 목록을 확인하세요.

~~~bash
gemini extensions list
~~~

im-not-ai가 목록에 있으면 다시 설치할 필요가 없습니다.

#### GitHub에서 내려받을 수 없다는 오류가 나오는 경우

다음 사항을 확인하세요.

1. 명령어를 줄바꿈 없이 한 줄로 입력했는지 확인합니다.
2. URL을 다음과 정확히 비교합니다.

~~~text
https://github.com/epoko77-ai/im-not-ai.git
~~~

3. 인터넷 연결을 확인합니다.
4. 1~2분 뒤 같은 명령어를 다시 시도합니다.

#### 설치는 됐는데 /humanize-korean이 없다고 나오는 경우

Gemini CLI가 새 확장 기능을 아직 읽지 않았을 수 있습니다.

1. Gemini CLI를 종료합니다.
2. 터미널을 닫았다가 새로 엽니다.
3. gemini를 다시 실행합니다.
4. /extensions list로 im-not-ai가 보이는지 확인합니다.

---

## 5. 설치한 im-not-ai 사용하기

### 5-1. Gemini CLI 다시 실행

터미널에서 다음을 입력합니다.

~~~bash
gemini
~~~

**이미 로그인했다면 매번 로그인할 필요는 없습니다.** 로그인 정보가 컴퓨터에 저장되어 다음부터는 바로 사용할 수 있습니다.

### 5-2. 가장 쉬운 사용법: 자연어로 요청하기

Gemini 화면에서 다음처럼 입력합니다.

~~~text
아래 글의 사실, 수치, 고유명사와 의미는 바꾸지 말고, AI가 쓴 티가 덜 나도록 자연스러운 한국어로 윤문해 줘.

[여기에 윤문할 글을 붙여넣으세요]
~~~

설치한 확장 기능이 정상적으로 읽혔다면 글을 분석하고 윤문한 결과를 보여 줍니다.

### 5-3. 전용 명령어로 사용하기

다음처럼 입력할 수도 있습니다.

~~~text
/humanize-korean
~~~

그다음 윤문할 글과 요청 사항을 입력합니다.

~~~text
/humanize-korean

다음 글을 자연스러운 한국어로 윤문해 줘.
사실, 수치, 고유명사, 직접 인용은 바꾸지 말고 원문의 뜻을 유지해 줘.

[윤문할 글]
~~~

버전에 따라 /humanize-korean 뒤에 바로 내용을 이어서 입력해도 됩니다.

~~~text
/humanize-korean 다음 글의 AI 티를 없애고 자연스럽게 다듬어 줘: [윤문할 글]
~~~

### 5-4. 결과가 마음에 들지 않을 때

같은 Gemini 세션에서 다음처럼 추가 요청을 할 수 있습니다.

~~~text
원문의 말투를 더 많이 유지하면서 다시 윤문해 줘.
~~~

또는 다음처럼 요청할 수 있습니다.

~~~text
번역투만 더 줄이고, 내용과 문단 구조는 그대로 유지해 줘.
~~~

~~~text
수정한 부분을 먼저 간단히 설명하고, 그다음 최종 윤문본을 보여 줘.
~~~

### 5-5. 긴 글을 붙여넣을 때

긴 글은 한 번에 붙여넣을 수 있지만, 컴퓨터나 터미널 종류에 따라 붙여넣기가 느릴 수 있습니다.

- macOS: 보통 Command(⌘) + V

붙여넣은 뒤 바로 답변이 나오지 않아도 잠시 기다리세요. 글이 길면 처리에 시간이 걸릴 수 있습니다.

붙여넣기가 중간에 끊기거나 글자가 이상하게 보이면 다음 방법을 시도하세요.

1. 글을 짧은 단위로 나누어 처리합니다.
2. 한 번에 한 문단만 먼저 테스트합니다.
3. 터미널 창을 새로 열고 Gemini CLI를 다시 실행합니다.

### 5-6. 결과를 복사하는 방법

결과가 터미널에 표시되면 마우스로 필요한 부분을 선택한 뒤 복사합니다.

- macOS: 선택 후 Command(⌘) + C

터미널에서 Ctrl+C는 복사가 아니라 실행 중인 작업을 중단하는 단축키로 작동할 수 있습니다. 결과를 복사할 때는 마우스 오른쪽 버튼의 Copy 메뉴를 사용하는 편이 안전합니다.

---

## 매번 사용할 때의 가장 짧은 순서

설치를 모두 끝낸 뒤에는 다음 네 단계만 기억하면 됩니다.

1. 터미널 열기
2. 다음 입력

~~~bash
gemini
~~~

3. Gemini 화면에서 다음 입력

~~~text
/humanize-korean
~~~

4. 윤문할 글 붙여넣기

**Google 계정 로그인과 im-not-ai 설치는 보통 처음 한 번만 하면 됩니다.**

---

## 전체 설치 명령어만 다시 보기

Node.js와 npm이 이미 설치되어 있다는 전제에서 일반 터미널에 입력할 명령어는 다음 두 줄입니다.

~~~bash
npm install -g @google/gemini-cli
gemini extensions install https://github.com/epoko77-ai/im-not-ai.git
~~~

그다음 Gemini를 실행합니다.

~~~bash
gemini
~~~

Gemini 화면에서 사용합니다.

~~~text
/humanize-korean
~~~

---

## 문제를 해결할 때 가장 먼저 확인할 것

문제가 생기면 오류 메시지 전체를 먼저 확인하세요. 특히 다음 네 명령어의 결과가 중요합니다.

~~~bash
node --version
npm --version
gemini --version
gemini extensions list
~~~

정상이라면 각각 버전 숫자, 버전 숫자, Gemini CLI 버전 숫자, 설치된 확장 기능 목록이 나옵니다.

오류 메시지를 다른 사람에게 보여 줄 때는 다음 정보는 지우고 공유하세요.

- 이메일 주소
- API 키
- 액세스 토큰
- 개인 파일 경로
- 비공개 글 내용

오류 메시지의 첫 줄과 마지막 몇 줄만으로도 원인을 파악할 수 있는 경우가 많습니다.

---

## 삭제하거나 업데이트하고 싶을 때

### im-not-ai 업데이트

일반 터미널에서 다음을 입력합니다.

~~~bash
gemini extensions update im-not-ai
~~~

### im-not-ai 삭제

~~~bash
gemini extensions uninstall im-not-ai
~~~

### Gemini CLI 업데이트

~~~bash
npm install -g @google/gemini-cli@latest
~~~

업데이트 후에는 Gemini CLI를 종료했다가 다시 실행하세요.

---

## 공식 문서

- [Gemini CLI 설치 공식 문서](https://geminicli.com/docs/get-started/installation/)
- [Gemini CLI Google 로그인 공식 문서](https://geminicli.com/docs/get-started/authentication/)
- [Gemini CLI 확장 기능 공식 문서](https://geminicli.com/docs/extensions/)
- [im-not-ai 설치 문서](https://github.com/epoko77-ai/im-not-ai/blob/main/INSTALL.md)
- [im-not-ai 저장소](https://github.com/epoko77-ai/im-not-ai)

Gemini CLI의 화면과 메시지는 버전에 따라 조금씩 바뀔 수 있습니다. 화면의 문구가 이 문서와 완전히 같지 않아도, Sign in with Google, extensions, im-not-ai처럼 핵심 단어가 보이는지 확인하면 됩니다.
