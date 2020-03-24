#  유용한 git 명령어

### git 초기화
- `git init` 
    - git 초기화작업이며, 현재 폴더에 Git저장소를 생성하는 명령어이다.
    - git init 진행후 버전관리가 가능해진다.
    - git 버전정보와 원격저장소 주소등이 들어있는 .git 폴더가 생성된다.
    - .git 폴더가 로컬 저장소가 되며, 이 로컬 저장소가 존재하는 현재 폴더는 **워킹트리**라고 한다.
    
### 옵션 확인/설정 하기
- `git config --list` 
   - 현재 프로젝트의 모든 옵션 살펴보기  
- `git config --global <옵션> ` 
    - 전역 옵션의 내용 보기  
    - `git config --global user.name` : 현재user.name 확인(git 커밋에 명시되는 이름)
    - `git config --global user.email` : 현재user.email 값 확인(git 커밋에 명시되는 이메일)
    - `git config --global core.editor` : 현재 사용중인 기본 에디터
    - ...
- `git config --global <옵션> <값> `
    - 전역 옵션에 새로운 값 설정하기
    - `git config --global user.name "myName"` : user.name을 myName 으로 설정
    - `git config --global user.email "emailAddr"` : user.email을 emailAddr 로 설정
- `git config --global --unset <옵션>` : 지정한 전역 옵션 삭제하기  
- `git config --local <옵션>` : 지역 옵션의 내용 보기  
- `git config --local <옵션> <값>` : 지역 옵션에 새로운 값 설정하기 내용 보기  
- `git config --local --unset <옵션>` : 지정한 지역 옵션 삭제하기  
- `git config --system <옵션>` : 시스템 옵션의 내용 보기  
- `git config --system <옵션> <값>` : 시스템 옵션에 새로운 값 설정하기 내용 보기  
- `git config --system --unset <옵션>` : 지정한 시스템 옵션 삭제하기
> 우선순위는 **지역 옵션 > 전역 옵션 > 시스템 옵션** 순으로 높다  

### 커밋 관련
#### add
- `git add 파일명` 
    - 커밋에 해당 파일을 추가하고 싶을때
    - `git add 파일1 파일2 ...` : 파일1, 파일2, ..을 스테이지에 추가하기
    - `git add .` : 변경된 모든 파일이 스테이지에 올라간다. (=커밋될 목록에 추가된다)
#### commit
- `git commit` 
    - 스테이지에 있는 파일들을 커밋한다.
- `git commit -a` 
    - add 명령을 생략하고 바로 커밋할때 사용하는 명령어
    - 변경된 파일과 삭제된 파일이 자동으로 0스테이징에 올라가 커밋된다.
    - untracked 파일은 커밋되지 않는다.
    > **tracked 상태** : 한번이라도 Git에 올렸던 상태(한번이라도 add를 한 상태)
- `git commit -m "커밋메세지"` 
    - 커밋하기 (이때 커밋 상세 설명은 '커밋메세지'가 된다.)
    
#### push
- `git push [-u] [원격저장소별명] [브랜치이름]`
    - 로컬저장소에 잇는 커밋들을 원격저장소에 올리기(푸시하기)
    - 예 ) git push -u origin master == git push origin master
    - `git push` : 한번 등록한 후에는 git push 만 입력해도된다.

#### pull
- `git pull`
    - 원격저장소의 변경사항을 워킹트리에 반영
- `git pull origing master` 
    - 원격지 master 브랜치에 있는 커밋들을 로컬로 내려받기

#### fetch
- `git fetch [원격저장소별명] [브랜치이름]`
    - 원격저장소의 브랜치와 커밋들을 로컬저장소와 동기화
    - `git fetch` : 모든 원격저장소에서 모든 브랜치를 가져오기
#### merge
- `git merge 브랜치이름` 
    - 지정한 브랜치의 커밋들을 현재 브랜치 및 워킹트리에 반영
#### reset
- `git reset [--hard/soft/mixed] [파일명]`
    - `git reset` : 옵션을 생략할 경우 mixed reset으로 작동한다. 이때 스테이지 영역에 있는 파일들을 단순히 언스테이징 한다.
    - `git reset --hard HEAD~2` : HEAD를 두 커밋 이전 커밋으로 옮긴다. 이때 변경된 파일들은 모두 변경전 상태로 초기화 된다.              

#### log
- `git log` 
    - 커밋 이력 확인
    - `git log -n` : 최신순으로 n개의 커밋로그만 보는 명령어
    - `git log --oneline --graph --all --decorate` 
        - 모든 브랜치들의 로그를 간결하고 예쁘게 보여준다
        - --oneline : 커밋메세지를 한줄로 요약해서 보여준다.
        - --garph : 커밋 옆에 브랜치의 흐름을 그래프로 보여준다.
        - --decorate : 브랜치와 태그 등의 참조를 간결히 표시한다.
        - --all : all 옵션이 없을 경우 HEAD와 관계없는 옵션은 보여주지 않는다.
#### clone
- `git clone https://github.com/himj131/gittutorial.git` 
    - 원격 저장소에 있는 프로젝트를 로컬에 내려받기
    - 해당 위치에 레파지토리 프로젝트명(gittutorial)과 동일한 폴더가 생성된다.
- `git clone https://github.com/himj131/gittutorial.git .` 
    - 원격 저장소에 있는 프로젝트를 현재 폴더에 내려받기
    - 원격 저장소이름과 로컬에서 사용할 프로젝트 폴더명을 다르게 하고싶을 경우 사용한다.
- `git clone https://github.com/himj131/gittutorial.git [폴더명]`
    - 원격 저장소에 있는 프로젝트를 폴더명에 내려받기
    - 폴더명에 해당하는 폴더가 없는경우 새로 생성된다.
    

### 브랜치 관련
- `git branch` : 브랜치 목록 보기
    - `git branch -v` : 브랜치 목록과 각 브랜치 마지막 커밋도 함께 보기
    - `git branch [-f] newbranch` : newbranch라는 이름의 신규 브랜치 생성
    - `git branch -r[v]` : 원격 저장소에 있는 브랜치 보기 (v 옵션시 마지막 커밋 함께 보기)
    - `git branch -d 브랜치명` : 브랜치 삭 
- `git checkout 브랜치명` : 특정 브랜치가 가르키고 있는 커밋의 내용을 워킹트리에 반영하기
- `git checkout 커밋아이디` 
    - 해당커밋 아이디의 커밋상태로 코드를 되돌린다.
    - HEAD와 브랜치가 분리되는 Detached HEAD 상황이 되어 Detached HEAD의 커밋들은 안보이게 된다.(git checkout 브랜치명 으로 해결가능)
    - 이 방법보다는 브랜치명으로 checkout 하는것을 권장하고 있다.
- `git checkout -` 
    - 직전 커밋 상태의 코드로 되돌리기
- `git remote add origin https://github.com/himj131/gittutorial.git` 
    - 로컬 저장소에 원격 저장소의 주소(https://github.com/himj131/gittutorial.git)를 연동
    - 원격저장소의 이름은 origin이 된다.(origin은 다른 이름으로 변경 가능)
- `git remote -v` : 원격 저장소 목록 확인

### 태깅
- `git tag -a -m 메세지 태그이름 [브랜치 또는 체크섬]` : -a 로 주석있는 태그 생성. 브랜치이름을 생략하면 HEAD에 태그를 생성한다.

### 기타
- `git help <명령어>` 
    - 해당 명령어의 도움말을 표시한다.
    - 예) git help commit

- `git status`
    - git 상태보기햣 ㅎㅎ
    - `git status -s` : 짧게 요약해서 상태를 보여줌, 변경된 파일이 많을 때 유용하다.