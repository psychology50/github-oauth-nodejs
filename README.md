```bash
$ cd ./github-oauth-nodejs

$ npm install
```

프로젝트 파일 경로 안에 .env 파일 생성 후
```
GITHUB_CLIENT=깃헙_클라이언트_코드
GITHUB_SECRET=깃헙_시크릿_코드
```

끝났으면, app.js 실행

```bash
$ node app.js
```

브라우저 열고 `http://localhost:3000/oauth/github` 입력  
→ Github 로그인  
→ 로그창에 User 데이터 잘 받아왔는지 확인 (혹은 임시 토큰..? 아무거나 상관 없습니다.)


Client Application 내부 구성입니다.
참고로 현재 API는 http://localhost:8081/api/v1/users/login 쪽으로 쐈는데, 경로 다르면 수정해주시면 됩니다.


```javascript
// ./controller/oauth.js
export const githubLoginWithServer = async (req, res) => {
    console.log("log : start githubLoginWithServer");
    const { code } = req.query;
    const baseUrl = "http://localhost:8081/api/v1/users/login"; // <--- 이부분
    const body = {
        client_id: process.env.GITHUB_CLIENT,
        client_secret: process.env.GITHUB_SECRET,
        code,
    }
```
