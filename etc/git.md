# git 이란?


- 형상 관리 도구 (Configuration Management Tool)
- 버전 관리 시스템
- 분산형 관리 시스템

<br>

### Getting Started
----


_**Download for macOS**_

- Install Homebrew -> [바로가기](https://brew.sh/)

- ``` $ brew install git ```

<br/>

_**homebrew란**_
macOS 용 패키지 관리 애플리케이션

<br>

### Config git
----

- 전역 설정 세팅
    ``` $ git config --global user.name "yeonnnee" ``` <br />
    ``` $ git config --global user.email yeonnnee@gmail.com ```


- 세팅 확인
    ``` $ git config —list ```


- 전역 설정 삭제
    ``` $ git config --global --unset user.name ``` <br />
    ``` $ git config --global --unset user.email ```

<br>

### Setting SSH

계정 주인이 본임임을 보증을 위해서 [SSH](./ssh.md) 공개키로 인증

- ``` % ssh-keygen ``` 명령어를 입력

- ``` % cat ~/.ssh/id_rsa.pub ``` 로 공개키 확인
- gitHub > settings > SSH and GPG keys 에 등록
 
<br>

### git command

| command    | DESC      | Example        |
| --------- | ----------- | ---------------|
| tig       | git 상태 파악 | git tig |
| push      | local에서 commit 한 내용 remote에 반영 | git push origin 브랜치 명
| pull      | local branch 와 remote branch 병합 | git pull  
| merge     | local branch 와 local branch 병합 | 
| commit    | stage된 변경사항 저장    |
| add       | unstage인 변경사항을 stage로    |
| reset     | head를 옮기는 것    | - reset HEAD~숫자 -> 숫자만큼 뒤로 이동 <br/> - reset HEAD 일련번호 -> 일련번호로 이동 <br/>- HEAD -> stage된 변경사항을 unstage로 변경
| rebase    | 시작점 옮기는 것으로 다른 branch 업데이트 내용 적용시 사용 | git checkout master <br /> > git pull origin master <br />  > git checkout 브랜치 <br />  > git rebase 타겟브랜치
| stash     | 임시저장 | stash pop : 임시저장 내용 불러오기 <br /> stash drop : 임시저장 내용 버리기 |
| cherry-pick | 특정한 커밋을 가져옴 | |
| checkout | branch 이동 <br/> 변경사항 있는 파일 변경 취소 <br /> branch 생성 | 
| abort | 이전에 실행한 명령어 취소 | git merge --abort
| reflog  | 로그 확인 | 


<br>
<br>

### Rebase 취소하는 방법

잘못 리베이스된 git이 remote까지 반영된 경우 취소해야 하는데 이때 reflog 와 reset을 사용하여 해결 할 수 있다.

<br>

:one: _**git reflog 브랜치명**_

    이 명령문은 잘못 rebase한 로컬 컴퓨터에서 실행해야 
    rebase 로그를 확인 할 수 있다.

:two: _**git reset --hard 128e6d4**_

    reflog를 보고 돌아가고 싶은 커밋명을 찾는다. 
    위의 명령문을 쓰고 이전 커밋 이력을 모두 reset 한다.

:three: _**git push -f origin 브랜치명**_

    리셋한 커밋이력을 리모트로 강제 푸시


