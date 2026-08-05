## 폴더명 만들기
> cmd창에서 mkdir 폴더명

> cd 폴더명 : 폴더 안으로 들어가기(하위폴더)
> cd .. : 폴더 밖으로 나가기(상위폴더)

#### cmd창에서(또는 해당 폴더에서 터미널 열기)
> code . : 지정된 폴더로 vs code 실행

#### vs code
> 작웝환경 갖추기
- GUI 크기 조절
- 코드 글자 크기 조절
- ctrl + ` : 터미널 실행

### Git
#### Git 버전 관리
> 작업을 진행하다보면 단계별 작업 내역을 남기면서 코드 관리를 해야할 필요가 있음  
> 여러개의 복사본을 물리적으로 만들어 관리하긴 힘드므로 Git을 활용하여 중요한 시점마다 기록을 남기고  
> 원하는 특정 시점으로 언제든 코드를 되돌리거나 원하는 시점에서 새로운 복사본을 만들기 위한 일련의 작업

#### Git을 쓰는 이유
> 작업의 단계별 히스토리를 남겨 코드의 유지보수의 효율성 증대  
> 여러명의 작업자가 하나의 프로젝트를 협업할때 작업자마다 복사본을 만들어 서로의 작업에 간섭을 미치지 않으면서 동일한 프로젝트를 수행하기 위함

#### GitHub란
> Git으로 버전관리한 작업물을 클라우드 공간에 저장하여  코드의 공유 및 코드의 변경사항을 GUI상에서 직관적으로 파악하기 위한 오픈소스 형태의 클라우드 저장 공간
> 원격저장소라고도 불리우며 gitHub에 올라간 코드를 배포도 가능

#### Git 기본 명령어

- 설치된 깃 버전 확인
git --version

- 깃 유저명, 이메일 등록
git config --global user.name '사용자명'
git config --global user.email '이메일주소'
​
- 시스템에 등록된 사용자명, 이메일주소 확인
git config user.name
git config user.email
​
- 작업 폴더로 이동후 깃 초기화
git init
​
- 현재 git 상태 확인
git status
​
- 파일 tracking 시작  (Stage Area에 등록)
git add .

- 커밋 메세지 작성 (변경 사항에 대한 메세지 작성 후 되돌리기 포인트 생성)
git commit -m '커밋 메세지'
​
- 커밋 내역 확인
git log
​
- 원하는 시점의 커밋 확인
git checkout 커밋아이디(해쉬코드)

#### 특정 파일 및 폴더 깃 상태관리에서 제외
- 작업 폴더 내에 .gitignore파일 생성  
> 작업 폴더내 특정 피일을 제외
abc.txt  
> 작업 폴더내 특정 확장자 파일은 모두 제외  
*.확장자명  
> 작업 폴더내 특정 폴더를 제외  
/폴더명

#### 커밋 되돌리기
커밋 되돌리기에는 크게 reset과 revert 두가지 방법이 존재

- reset : 특정 커밋시점으로 되돌린 후 그 이후 커밋을 제거   (reset으로 되돌린 커밋 내역 이후 기록 초기화됨)

- revert : 기존 커밋  내역을  유지하면서 특정 커밋 시점으로 코드 되돌림  
(resolve conflict 필요)

- reset으로 커밋 되돌리기  
> 직전 한개의 커밋 되돌림
git reset HEAD^ --hard  
> 3단계 이전의 커밋으로 되돌림
git reset HEAD~3 --hard  
> 원하는 커밋 시점으로 되돌림
git reset 커밋아이디(해쉬코드)

- reset으로 커밋을 되돌리면 로컬 저장소에 비해 원격 저장소의 커밋이 더 최신이기 때문에 git push가 불가능 하므로 다음의 명령어로 강제로 push  
git push origin master  -f

- revert로 커밋 되돌리기  
git revert 커밋 아이디


#### Branch  
하나의 프로젝트에서 버전별로 복사본을 생성

- 브랜치 생성  
git branch 브랜치명
​
- 브랜치 확인  
git branch -v
​
- 특정 브랜치로 이동  
git checkout 브랜치명
​
- 원격 저장소의 특정 브랜치 가져오기  
git pull origin 브랜치명  
> 특정 브랜치를 가져온다음 checkout까지 해줘야 활성화됨  
git checkout 브랜치명

- 특정 브랜치 삭제  
git branch -d 브랜치명
​
- 삭제된 브랜치 원격저장소에 반영  
git push origin :삭제한 브랜치명
​
- 브랜치 병합
> 마스터 브랜치로 이동한 상태에서  
> merge시 합치려고 하는 브랜치에서 동일한 위치의 코드를 변경해야 될 시 충돌방생 (Conflict)
> Conflict발생시 수작업으로 적용할 코드를 수정 (resolve conflict)  
git merge 합칠 브랜치명


#### 원격 저장소에 작업물 등록

- 원격 저장소 등록  
git remote add origin 원격저장소URL

- 원격 저장소에 업로드  
> 특정 브랜치 업로드  
git push origin 브랜치명  
> 생성된 모든 브랜치 업로드  
git push origin --all
​
- 원격 저장소의 내용을 내려받아 동기화하기  
git pull origin 브랜치명

- 원격 저장소의 내용을 통채로   복사해서 내려받기  
git clone 원격저장소URL  

#### Pull과 Clone의 차이
Pull : 이미 로컬저장소와 원격저장소가 연결되어 있는 상태에서 원격 저장소의 새롭게 바뀐 내용만 내려받아 동기화  
Clone : 원격저장소는 있는데 로컬저장소가 없는 경우 통으로 프로젝트를 복사해서 내려받음

#### push로 업로드시 오류가 발생하는 경우
보통 로컬 저장소보다 원격 저장소의 커밋이 더 최신의 내용일 경우 push 오류 발생하기 때문에 이떄는 먼저 원격 저장소 내용을 pull로 가져와서 동기화한뒤 다시 다시 push 로 업로드