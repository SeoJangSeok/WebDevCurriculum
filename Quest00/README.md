# Quest 00. 형상관리 시스템

# start

## Introduction

- git은 2021년 현재 개발 생태계에서 가장 각광받고 있는 버전 관리 시스템입니다. 이번 퀘스트를 통해 git의 기초적인 사용법을 알아볼 예정입니다.

## Topics

- git
  - `git clone`, `git add`, `git commit`, `git push`, `git pull`, `git branch`, `git stash` 명령
  - `.git` 폴더
- GitHub

## Resources

- [Resources to learn Git](https://try.github.io)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=ko)
- [Inside Git: .Git directory](https://githowto.com/git_internals_git_directory)

## Checklist

- 형상관리 시스템은 왜 나오게 되었을까요?
  > 소프트웨어의 변경사항을 체계적으로 추적하고 통제하기 위해서.
  > 어떠한 문서나 파일이 변경된 경우에 변경된 내용과, 원인을 기록해 놓고 나중에 필요한 경우 찾아 볼 수 있도록 관리한다.
  > 버전관리(Version Management)라고도 하는데 형상관리(Configuration Management)가 더 포괄적인 의미를 지닌다.
- git은 어떤 형상관리 시스템이고 어떤 특징을 가지고 있을까요? 분산형 형상관리 시스템이란 무엇일까요?
  > git은 분산형 형상관리 시스템이다.
  > 분산형 버전관리 시스템 : 중앙에서 관리하고 있던 모든 이력들을 가진 저장소 전체를 복사하여 사용자의 컴퓨터로 가져와 사용한다.
  > 사용자의 컴퓨터에서는 local로 개발을 할 수 있으며, 이를 중앙 서버로 보낼 수도 있고 주앙 서버의 진행상황을 사용자의 컴퓨터로 갱신시켜서 사용할 수도 있다.
  > 중앙 서버에 문제가 생겨도 사용자의 local 저장소에 저장된 데이터로 복구시키기가 용이하며 공동작업을 하는 팀원들 모두가 이러한 저장소 정보를 갖고 있으므로 서버와 일부 사용자의 데이터가 날아가도 복구가 가능하다.
  - git은 어떻게 개발되게 되었을까요? git이 분산형 시스템을 채택한 이유는 무엇일까요?
    > git이 만들어 지기 전, Linux 커널은 BitKeeper라고 하는 분산 버전관리 시스템을 사용하고 있었는데, Linux 커뮤니티 내의 한 개발자가 BitKeeper의 통신 프로토콜을 리버스 엔지니어링(컴파일된 결과파일에서 소스를 거꾸로 읽어 내는 방법)하여 해킹을 하는 사건이 발생해 BitKeeper와 Linux 커뮤니티 사이에 갈등이 발생하게 됐다. 이에 BitKeeper는 Linux 커뮤니티에 더이상 공짜로 BitKeeper를 사용할 수 없도록 라이센스를 제한하게 되고, 이에 당장 BitKeeper를 대체할 버전관리 시스템이 필요했던 리누스 토발즈는 BitKeeper의 장점과 개선사항을 개선하여 개발한게 git이다.
- git과 GitHub은 어떻게 다를까요?
  > git : git은 코드와 코드의 수정내역을 기록하고 관리할 수 있는 버전관리 프로그램이고, '로컬'에서 기록을 스스로 관리할 수 있도록 해준다. git을 통해 브랜치를 생성하고 이전 브랜치로 복구, 삭제, 병합이 가능하다. 로컬 저장소를 사용하기 때문에 다른 개발자와 실시간으로 작업을 공유할 수 없다.
  > Github : Github는 git 저장소를 관리하는 클라우드 기반 호스팅 서비스이다. git 저장소 호스팅 서비스는 클라우드 기반으로 다른 사람과 소스코드 공유가 가능하며, git의 기본적인 기능을 확장하여 제공한다. 클라우드 서버에 소스를 올리기 때문에 프로젝트에 여러 명의 사람이 참여하여 버전 제어 및 공동 작업이 가능하다.
- git의 clone/add/commit/push/pull/branch/stash 명령은 무엇이며 어떨 때 이용하나요? 그리고 어떻게 사용하나요?
  > $ git clone https://github.com/[계정명]/[프로젝트명].git : 원격저장소에서 프로젝트를 내 로컬 환경으로 복사해서 가져온다.
  > git add : 작업 영역(working directory) 상의 변경 내용을 스테이징 영역(staging area)에 추가하기 위해 사용하는 명령어. 다음 변경(commit)을 기록할 때까지 변경분을 모아놓기 위해 사용한다.(git commit 명령어를 통해 명시적으로 기록을 남기기 전까지는 git add를 많이 실행해도 git 저장소의 변경 이력에는 어떤 영향도 없다)
  > $ git add. (현재 위치에 있는 모든 파일을 add)
  > $ git add '파일명' (특정 파일만 add)
  > git commit : staging area에 있는 변경 내용들을 local 저장소에 버전(기록)을 남기기 위해 사용한다.
  > $ git commit -m "<message>" (메시지를 남기는 이유는 commit에 대한 정보 기록!)
  > git push : 원격 저장소(remote repository)에 변경 내용을 업로드하기 위해서 사용한다. push를 하면 Github에서 코드 확인이 가능하다.
  > $ git push -u origin <브랜치명> (-u 옵션을 최초에 사용하면 나중에 push할 때 git push 명령어만 사용할 수 있다. [인자 생략])
  > git pull : 원격 저장소에서 로컬 저장소로 소스를 가져오는 명령어로, 원격 저장소의 소스가 현재 내 소스보다 최신 버전이라면 지금의 버전을 최신으로 맞춘다.
  > $ git pull origin <브랜치명>
  > git branch : 동일한 저장소 내의 소스에 대해 서로 영향을 받지 않는 독립적인 공간이다.
  > $ git branch <브랜치명> (-M 옵션을 사용하면 branch의 이름을 기본적으로 <브랜치명>으로 정한다.)
  > git stash : 아직 마무리하지 않은 작업을 스택에 잠시 저장할 수 있도록 하는 명령어. 이를 통해 아직 완료하지 않은 일을 commit하지 않고 나중에 다시 꺼내와 마무리할 수 있다.
  > $ git stash (변경 내용 임시 저장, 스택에 새로운 stash가 만들어지고 working directory는 깨끗해진다.)
  > $ git stash list (저장한 stash 목록을 확인할 수 있다.)
  > $ git stash apply (가장 최근의 stash를 가져와 적용한다.)
- git의 Object, Commit, Head, Branch, Tag는 어떤 개념일까요? git 시스템은 프로젝트의 히스토리를 어떻게 저장할까요?
  > Object : Git의 핵심은 단순한 key-value(ex.파일 이름-파일 데이터)데이터 저장소이다. 어떤 형식의 데이터라도 집어넣을 수 있고 해당 key로 언제든지 데이터를 불러올 수 있다.
  > Commit : 작업한 내용들을 저장소에 저장하는 것.
  > Head : 현재 접속한 브랜치를 포인터로 가르키고 있는 것. 해당 브랜치에는 최신 커밋에 대한 해쉬값을 가지고 있다.
  > Branch : 모든 버전 관리 시스템은 브랜치를 지원한다. 원래 코드와는 상관없이 독립적으로 개발을 진행할 수 있는데, 이렇게 독립적으로 개발하는 것이 브랜치이다.
  > Tag : 커밋을 참조하기 쉽도록 알기 쉬운 이름을 붙이는 것.
  > 일반 태그(Lightweight tag) : 이름만 붙일 수 있다.
  > 주석 태그(Annotated tag) : 이름, 태그에 대한 설명, 서명, 이 태그를 만든 사람의 이름, 이메일과 태그를 만든 날짜 정보도 포함할 수 있다.
  > git은 데이터를 저장할 때 데이터와 헤더로 생성한 SHA-1 체그섬으로 파일 이름을 짓는다. 해시의 처음 두 글자를 따서 디렉토리 이름에 사용하고 나머지 38글자를 파일 이름에 사용한다.
- 리모트 git 저장소에 원하지 않는 파일이 올라갔을 때 이를 되돌리려면 어떻게 해야 할까요?
  > $ git rm <파일명> (로컬 디렉토리와 git 저장소에서 모두 삭제)
  > $ git rm --cached <파일명> (git 저장소에서만 삭제)
  > 옵션
  > -f : 변경사항을 커밋하지 않았을 경우 강제로 삭제.
  > -r : 디렉토리 삭제 ex) git rm -r directory1
  > 삭제 후, commit -> push (commit을 해주어야 변경된 내용을 저장할 수 있다)

## Quest

- GitHub에 가입한 뒤, [이 커리큘럼의 GitHub 저장소](https://github.com/KnowRe-Dev/WebDevCurriculum)의 우상단의 Fork 버튼을 눌러 자신의 저장소에 복사해 둡니다.
- Windows의 경우 같이 설치된 git shell을, MacOSX의 경우 터미널을 실행시켜 커맨드라인에 들어간 뒤, 명령어를 이용하여 복사한 저장소를 clone합니다.
  - 앞으로의 git 작업은 되도록 커맨드라인을 통해 하는 것을 권장합니다.
- 이 문서가 있는 폴더 바로 밑에 있는 sandbox 폴더에 파일을 추가한 후 커밋해 보기도 하고, 파일을 삭제해 보기도 하고, 수정해 보기도 하면서 각각의 단계에서 커밋했을 때 어떤 것들이 저장되는지를 확인합니다.
- `clone`/`add`/`commit`/`push`/`pull`/`branch`/`stash` 명령을 충분히 익혔다고 생각되면, 자신의 저장소에 이력을 push합니다.

## Advanced

- Mercurial은 어떤 형상관리 시스템일까요? 어떤 장점이 있을까요?
- 실리콘밸리의 테크 대기업들은 어떤 형상관리 시스템을 쓰고 있을까요?
