# studyGit
## github의 기본 사용법
<br>

### 1. git 

git 은 컴퓨터의 파일의 변경 사항을 추적하는 장치이다.
<br>

### 2. github

github 는 웹호스팅 서비스로, git 툴을 사용하는 프로젝트를 지원한다. (쉽게 git을 웹으로 사용할 수 있도록 만들어진 서비스)
<br>

### 3. Repository

레포지트리는 말 그대로 저장소. 나의 프로젝트 파일들을 저장할 곳이다. 
<br>

### 4. Branch

레포지트리 전체의 버전 관리를 가능케한다. 협업시 다양한 업그레이드, 디버깅으로 인한 다양한 버전들이 생겼을 때 하나의 레포지트리에서 수정을 하는 것은 비효율적이기 때문. Gitflow 와 같이 전략적으로 운용한다.

상위 단계의 브랜치를 복제하며 생성된다. branch 내부에서의 변경사항을 commit 후 push 를 통해 반영했다면, branch 끼리의 변경사항을 반영해야할 때, 즉 브랜치들을 병합해야할 때는 merge 를 사용한다.

Merge 는 중요하니까.. (충돌 등 경우의 수가 많기에) push 후 관리자에게 pull request (PR) 을 보낸다. 이를 받은 관리자는 merge 를 하게되고 최종적으로 수정사항이 master 브랜치에 반영된다.
<br>

### 5. Repository 와 로컬 컴퓨터 작업 환경의 연결

(0901 Sourcetree 를 이용해 시도했으나, ssh 키 관리를 어떻게 하는지 잘 몰라.. (레포를 늘릴 때마다 각기 다른 키가 필요하나?) git bash 사용. git bash는 콘솔창과 같은 모양으로, $ 뒤에 명령어를 입력하여 이용한다. git 의 설치는 기본값으로 진행하였다.

우선 제대로 설치가 되었는지 확인을 한다.

```
$ git
```
#### 위 코드는 git 에서 사용 가능한 명령어 리스트를 형성한다.
제대로 설치 확인이 되었다면, 미리 저장 폴더를 원하는 위치에 생성하고 이곳에 깃헙의 파일을 복제하여 넣는 과정을 진행한다.

```
$ cd (디렉토리 주소)
```
#### 위 코드는 뒤에 쓰여진 디렉토리 주소로 이동하는 코드이다.

```
$ pwd
```

참고로 pwd 명령어는 현재 내가 어떤 디렉토리에 존재하는지 확인하는 명령어이다. 

여기까지 확인하여 작업 공간을 마련하고 그곳으로 잘 들어왔다면, 이제 본격적으로 복제를 진행하자.

```
$ git clone (레포지토리 주소)
```

#### 위 코드는 깃허브의 레포지토리 파일들을 현재 내가 위치한 로컬 디렉토리로 복제하는 코드이다.
뭔가 다운로드 되는 반응이 나오면 성공..

```
$ ls -al
```

#### 위 코드는 숨겨진 파일들을 포함한 디렉토리 내의 파일들과 디렉토리의 상세 정보를 확인하는 코드이다. 
참고로 이는 ls(디렉토리 내의 파일 출력), -a (숨겨진 파일 보기), l(디렉토리의 상세 정보) 등 총 3가지 코드가 합쳐진 결과물이다.

이제 깃헙의 모든 파일이 로컬로 옮겨졌으니 작업을 진행한다.

### 6. Commit & Push 방법

push 이전에, 로컬 컴퓨터의 디렉토리 내에 새로운 파일을 생성했을 경우에 이를 git에서 추적하도록 추가하는 작업이 필요하다. (이를 안하면 반영이 안되며, git에서 찾지 못한다.)


```
$ git add (파일 명 ex. index.html)
```

#### 위 코드를 통하여 특정 파일을 깃에 추가할 수 있다.

모든 변경한 작업 파일을 git이 볼 수 있게 하였다면 이제 commit & push 를 할 준비가 되었다. 이는 매우 간단하다.

```
$ git commit -m " 넣고 싶은 메세지 "
```
#### 위 코드를 사용하여 커밋을 진행하며, 커밋에 대한 메세지를 넣을 수 있다.

다만 여기서 끝나면 원격 저장소에는 변함이 없다. commit 은 변경 내용을 저장하는 기능일 뿐이다. (새로운 버전 저장)

```
$ git push origin master (main)
```

#### 위 코드를 사용하면 본 레포지토리 주소의 master(main) 브랜치에 변동사항이 push 된다.
origin master 는 매개 변수로 생략이 가능한데, origin 은 말 그대로 원본을 뜻한다. 즉 레포지토리를 복제한 상태의 복제본에서 작업을 진행했으므로, origin 은 깃헙의 원본 레포지토리를 뜻한다.(레포지토리의 기본 이름) 이는 clone 을 통해 자동으로 등록된다. 뒤에 붙는 것은 브랜치 이름. 이는 현재 체크아웃 중인
 브랜치에서 변동 사항이 없을 경우 생략이 가능하다.
```
$ git pull
```

#### 위 코드를 사용하면 변동사항이 반영된 깃헙의 레포지토리를 내 로컬 저장소로 가져올 수 있다.
이는 fetch 와 merge 를 연달아 진행하는 명령어이다. 먼저 fetch 의 경우, 원격 저장소의 변동 사항을 로컬 저장소로 가져올 때 FETCH_HEAD 라는 임시 브랜치를 만든다. 이후 이를 현재 체크아웃된 브랜치로 merge 하는 작업을 진행하여 로컬 저장소의 브랜치로 변동사항이 저장된다. pull 은 이를 한번에 진행할 수 있는 코드이다.

또한 git pull 뒤에도 매개변수가 들어가나, 현재 체크아웃 중인 브랜치와 변동사항이 없을 경우 생략 가능하다.

### 5. Branch 변동 사항이 생겼을 경우 로컬 저장소에 반영하는 법

먼저 당장 내가 어떤 브랜치를 쓰고 있는지 확인하는 과정이 필요하다.

```
$ git branch
```

#### 위 코드를 사용하면 현재 내가 들어있는 브랜치가 *로 표시된다.

```
$ git checkout (옮길 브랜치)
```

#### 위 코드는 내가 접속해있는 브랜치를 변경한다.
브랜치를 변경하여 작업을 진행하며 추가된 파일이 생길 경우, $ git add 를 통해 다시 재등록 해주는 것을 잊지 말자..

### 6. branch 를 merge 하는 법

```
$ git merge (작업한 브랜치 명)
```

작업한 브랜치의 변동 사항을 상위 브랜치로 merge 해 반영한다. 물론 작업을 했었던 브랜치가 사라지진 않는다.

하다 보니까 점점 모르는게 많아지는데, 우선 스터디를 위해서는 github 에 작업 내역을 알릴 수 있도록 commit / push 만 되도 당장은 부족함 없으므로... studyGit 은 일단 여기까지 (21.09.03)

### 추가 궁금했던 점

윈도우에서 폴더의 파일 확장자 명은 존재하지 않는다.

따라서 폴더를 커밋 / push 하고 싶을 땐, 그냥 폴더 명을 "" 안에 넣으면 통으로 반영된다.
