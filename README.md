#  유용한 git 명령어

### git 초기화
- `git init` 
    - git 초기화작업이며, 현재 폴더에 Git저장소를 생성하는 명령어이다.
    - git init 진행후 버전관리가 가능해진다.
    - git 버전정보와 원격저장소 주소등이 들어있는 .git 폴더가 생성된다.
    - .git 폴더가 로컬 저장소가 되며, 이 로컬 저장소가 존재하는 현재 폴더는 **워킹트리**라고 한다.
    
### 옵션 확인/설정 하기
- `git config --global <옵션> ` 
    - 전역 옵션의 내용 보기  
    - `git config --global user.name` : 현재user.name 확인(git 커밋에 명시되는 이름)
    - `git config --global user.email` : 현재user.email 값 확인(git 커밋에 명시되는 이메일)
- `git config --global <옵션> <값> `
    - 전역 옵션에 새로운 값 설정하기
    - `git config --global user.name "myName"` : user.name을 myName 으로 설정
    - `git config --global user.email "emailAddr"` : user.email을 emailAddr 로 설정
- `git config --global --unset <옵션>` 
    - 지정한 전역 옵션 삭제하기  
- `git config --local <옵션>` 
    - 지역 옵션의 내용 보기  
- `git config --local <옵션> <값>` 
    - 지역 옵션에 새로운 값 설정하기 내용 보기  
- `git config --local --unset <옵션>` 
    - 지정한 지역 옵션 삭제하기  
- `git config --system <옵션>` 
    - 시스템 옵션의 내용 보기  
- `git config --system <옵션> <값>`
    - 시스템 옵션에 새로운 값 설정하기 내용 보기  
- `git config --system --unset <옵션>` 
    - 지정한 시스템 옵션 삭제하기  
- `git config --list` 
   - 현재 프로젝트의 모든 옵션 살펴보기  
    
    
- `git status`
    - git 상태보기
    - `git status -s` : 짧게 요약해서 상태를 보여줌, 변경된 파일이 많을 때 유용하다.
- `git add 파일명` 
    - 커밋에 해당 파일을 추가하고 싶을때
- `git add .` 
    - 변경된 모든 파일이 커밋될 목록에 추가된다.
- `git commit -m "커밋메세지"` 
    - 커밋하기 (이때 커밋 상세 설명은 '커밋메세지'가 된다.)
- `git log` 
    - 커밋 이력 확인
- `git checkout 커밋아이디` 
    - 해당커밋 아이디의 커밋상태로 코드를 되돌린다.
- `git checkout -` 
    - 직전 커밋 상태의 코드로 되돌리기
- `git remote add origin https://github.com/himj131/gittutorial.git` 
    - 로컬 저장소에 원격 저장소의 주소(https://github.com/himj131/gittutorial.git)를 연동
    - 원격저장소의 이름은 origin이 된다.(origin은 다른 이름으로 변경 가능)
- `git clone https://github.com/himj131/gittutorial.git` 
    - 원격 저장소에 있는 프로젝트를 로컬에 내려받기
    - 해당 위치에 레파지토리 프로젝트명(gittutorial)과 동일한 폴더가 생성된다.
- `git clone https://github.com/himj131/gittutorial.git .` 
    - 원격 저장소에 있는 프로젝트를 현재 폴더에 내려받기
    - 원격 저장소이름과 로컬에서 사용할 프로젝트 폴더명을 다르게 하고싶을 경우 사용한다.
- `git push origin master` 
    - 로컬저장소에 잇는 커밋들을 원격저장소에 올리기(푸시하기)
- `git pull origing master` 
    - 원격지 master 브랜치에 있는 커밋들을 로컬로 내려받기

