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

Node.js 서버 구축
client 파일과 같은 위치에 server 폴더를 만들고, 서버가 실행될 때 찾아갈 server.js, Router 폴더와 테스트를 위한 test.js를 만든다.

server.js 파일에 다음과 같이 작성
const express = require('express');
const app = express();
const test = require('.//Router/test');

app.use('/', test);

const port=5000; //React가 3000번 포트를 사용하기 때문에 node 서버가 사용할 포트넘버는 다른 넘버로 지정해준다.
app.listen(port, ()=>{console.log(`Listening on port ${port}`)});
test.js에 다음과 같이 작성
const express = require('express');
const router = express.Router();

router.get('/', (req, res)=>{
  res.send({ test: "hi"});
});

module.exports = router;
최상단 폴더위치(musical)에서 제대로 실행되는지 확인한다.
node ./server/server.js
웹 브라우저에서 http://localhost:5000/으로 접속해서 "hi"가 뜬다면 성공
추가적으로 nodemon, concurrently를 설치한다
nodemon: node 명령어는 파일을 변경할 때마다 이전 명령어를 종료하고 다시 실행해야하는 불편함이 있는데 nodemon을 이용하면 바로바로 업데이트 가능
concurrently: react 서버와 node 서버를 동시에 실행시키기 위한 모듈

npm install nodemon --save
npm install concurrently --save
(dev를 붙이면 local에서만 사용하겠다는 의미)

package.json에 추가적인 설정을 해준다.
  "scripts": {
    "server": "cd server && nodemon server",
    "client": "cd client && npm start",
    "start": "concurrently --kill-others-on-fail \"npm run server\" \"npm run client\""
  },
    "devDependencies": {
    "nodemon": "^2.0.7"
  },
    "dependencies": {
    "concurrently": "^6.0.0",
    "express": "^4.17.1",
  },
npm start를 실행하고 3000번, 5000번 포트로 접속해서 이상이 없다면 성공!



React + Node.js 연동하기
react와 node 서버 간에 데이터를 주고 받기 위해서는 프록시 모듈이 필요하다

Proxy: '대신'이라는 사전적 의미를 가지고 있으며 클라이언트와 서버 사이의 네트워크 통신을 '대리'로 수행하는 미들웨어이다.

프록시 설치 npm install htpp-proxy-middleware --save

프록시 설정을 위해 client/src에 setupProxy.js를 생성

const proxy = require('http-proxy-middleware');

module.exports = (app) => {
  app.use(
    proxy('/api', {  //도메인 api로 호출
      target: 'http://localhost:5000/', //통신할 서버의 도메인주소
      changeOrigin: true,
    })
  )
}
통신을 위한 axios 라이브러리 설치 npm install axios
Router/test.js 내용 수정
const express = require('express');
const router = express.Router();

router.get('/', (req, res)=>{
  res.send({ test: "hi"});
});

module.exports = router;
client/App.js 수정
import axios from "axios";
import { useEffect } from 'react';

function App() {
  const callApi = async()=>{
    axios.get("/api").then((res)=>{console.log(res.data.test)});
  };

  useEffect(()=>{
    callApi();
  }, []);
  
  return (
    <div className="App">
	...
    </div>
  );
}

export default App;
실행



