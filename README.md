# JobPlanner

# 외국인 취업 사이트 사용법 #

---

#### 해당 문서는 외국인 취업에 관한 공고 및 면접을 위한 준비 사이트로 아래와 같은 기능을 가지고 사이트에 대한 기능을 수행합니다. ####

---

### 가비아 서버 호스팅 ###

#### 서브넷 생성 ####

<img width="503" alt="image" src="https://github.com/user-attachments/assets/50c12af6-f350-4cfa-8d1e-ba9863cd81f6">

#### 가상서버 생성 ####

<img width="479" alt="image" src="https://github.com/user-attachments/assets/b94fe8b3-f5e7-4d49-a694-d34910ee685f">

- 생성시 우분투로 생성한다. (그래야 git clone 가능)

#### SSH 접근 확인 ####

1. ssh (서버 아이디)@(ip주소)
2. ssh root@45.115.154.197 (ssh -p 22 root@45.115.154.197)
- ID : root
- PASSWORD : _bM^Y8Y59Gcd

<img width="1008" alt="image" src="https://github.com/user-attachments/assets/bc71e77a-8187-47bc-a988-e62c8c5c00de">


#### 방화벽 생성 ####
<img width="500" alt="image" src="https://github.com/user-attachments/assets/75782941-1e68-4f4f-8f36-c997f8cab030">

---

#### express를 이용한 백엔드 구축 ####

- express 모듈을 사용하여 간편하게 백엔드 서버를 구축한다.
- express는 http와 connect 컴포넌트를 기반으로 하는 웹 프레임워크

1. npx create-react-app my app
2. npm install express

https://velog.io/@autumndr3ams/210802-React-Node.jsexpress-%EC%97%B0%EA%B2%B0%ED%95%98%EA%B8%B0

---

#### Nginx를 이용한 React 배포및 Reverse Proxy 서버 구축 ####

https://blog.naver.com/dlaxodud2388/223161852880


#### 서버 호스팅 OR 컨테이너 호스팅 ####

https://jaebins.tistory.com/12 
https://velog.io/@po_lygon/gabia-1 
https://m.blog.naver.com/rnwkfydwkd/221999580669

- cafe24 나 가비아에서 진행하는 방법으로 express 모듈 적용시켜 마운트 시켜줌으로써 작동하도록 한다 => 어떤 호스팅이 어울릴지는 고민 (일단 nodejs, express 사용하는 방식으로)

