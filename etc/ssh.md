# SSH 란?

- Secure Shell 의 약자

- 두 컴퓨터 간 통신을 할 수 있게 해주는 하나의 protocol.
- 서로 다른 컴퓨터들을 Shell 을 통해 통신하기 위해 필요한 protocol 중 하나

<br/>

##### 특징

- SSH 를 이용한 통신에서는 Client 와 Host 의 통신이 암호화 되어 있다.

- 암호화 과정
    - 대칭 암호화
    - 비대칭 암호화
    - 해쉬 함수

<br/>

##### Authentication
- Password
- RSA : 내 컴퓨터에 SSH 키를 생성하여 나의 Public Key 를 host 목록에 추가해 자동으로 나를 인증하는 방법

<br/>

##### SSH key 생성

:one: ```ls -al ~/.ssh ``` 로 SSH KEY 유무 파악

    ``` id_rsa.pub ``` 파일이 존재하면 이미 SSH Key가 존재하는 것

:two: ``` ssh-keygen -t rsa -b 4096 -C "깃헙이메일주소" ``` 로 생성

<br/>

#####  passphrase 란?
    RSA 방식의 단점은 누군가 내 컴퓨터를 컨트롤 할 수 있게 된다면, 
    내 컴퓨터에 있는 SSH Key를 가진 모든 시스템에 접근 권한이 생길 수 있다.
    이에 추가적으로 비밀번호를 설정하여 보안하는 것을 말한다.




