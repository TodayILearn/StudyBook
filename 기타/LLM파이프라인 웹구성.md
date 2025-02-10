# 프리티어 LLM 파이프라인 웹 구성 설명

- organization 만들기
- 레포지터리 하나를 만들기 → git 주소 복사하기
- 깃 설정
  ```bash
  # /docs/index.html
  git init
  git add .
  git commit -m "first commit"
  # 본인 git으로 바꾸기 (제발)
  git remote add origin https://github.com/zero-aqua-coke/my-llm-pjt.git
  git branch -M main
  git push -u origin main
  ```
- 배포

  Settings → Pages → Branch `None` ⇒ `Main` → `/root` ⇒ `/docs` → Save

- **STEP1**: Favicon, OG, 웹폰트, 부트스트랩

  - Favicon
    https://gemini.google.com/app
      <aside>
      ✨
      
      맛집 사이트과 어울리는 favicon용 이미지 생성 요청
      
      </aside>
      
      https://realfavicongenerator.net/
      
      assets 폴더 안에 favicon zip을 폴더 만들지 말고, 만들더라도 그 내용만 남겨라. zip 지우기
      
      ```bash
      unzip favicon.zip && rm favicon.zip
      ```
      
      ```html
      <link
        rel="icon"
        type="image/png"
        href="./assets/favicon-96x96.png"
        sizes="96x96"
      />
      <link rel="icon" type="image/svg+xml" href="./assets/favicon.svg" />
      <link rel="shortcut icon" href="./assets/favicon.ico" />
      <link
        rel="apple-touch-icon"
        sizes="180x180"
        href="./assets/apple-touch-icon.png"
      />
      <link rel="manifest" href="./assets/site.webmanifest" />
      ```
      
      ```bash
      git switch -c step1
      git add . # add 시 내가 어느 경로 있는지가 staging에 중요 (CLI라면)
      git commit -m "favicon"
      git push origin step1
      ```
      
      - push 했는데 반응이 없음. 그 이유는 main이 아니라 step1이라는 브랜치를 썼기 때문임을 인지함


  - OG
      <aside>
      ✨
      
      맛집 사이트와 어울리는 og tag preview용 이미지 생성 요청
      
      </aside>
      
      - 이름을 `preview.png` 로 수정 → assets에 해당 파일 넣기
      
      <aside>
      ✨
      
      preview.png를 미리보기로 하는 og tag 작성하고 맛집 사이트에 어울리게 미리 내용 채우기
      
      </aside>
      
      ```html
      <meta property="og:title" content="맛집 추천: 런치펀치" />
      <meta
        property="og:description"
        content="맛집 추천: 런치펀치는 전국 각지의 맛집을 소개하는 웹사이트입니다. 다양한 지역의 맛집을 한눈에 볼 수 있으며, 상세한 정보와 사진을 확인할 수 있습니다. 맛집을 찾을 때는 필수로 참고하는 사이트입니다."
      />
      <meta
        property="og:image"
        content="https://zero-aqua-coke.github.io/my-llm-pjt/assets/preview.png"
      />
      <meta
        property="og:url"
        content="https://zero-aqua-coke.github.io/my-llm-pjt/"
      />
      <meta property="og:type" content="website" />
      ```

  - 웹폰트

    https://noonnu.cc/font_page/pick

    style.css

    ```css
    @font-face {
      font-family: "Pretendard-Regular";
      src: url("https://fastly.jsdelivr.net/gh/Project-Noonnu/noonfonts_2107@1.1/Pretendard-Regular.woff")
        format("woff");
      /* font-weight: 400; */
      /* font-style: normal; */
    }

    @font-face {
      font-family: "PartialSansKR-Regular";
      src: url("https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2307-1@1.1/PartialSansKR-Regular.woff2")
        format("woff2");
      /* font-weight: normal;
        font-style: normal; */
    }

    * {
      /* font-family: "Pretendard-Regular"; */
      font-family: "PartialSansKR-Regular";
    }
    ```

    ```css
    @font-face {
      font-family: "Pretendard-Regular";
      src: url("https://fastly.jsdelivr.net/gh/Project-Noonnu/noonfonts_2107@1.1/Pretendard-Regular.woff")
        format("woff");
      /* font-weight: 400; */
      /* font-style: normal; */
    }

    @font-face {
      font-family: "PartialSansKR-Regular";
      src: url("https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2307-1@1.1/PartialSansKR-Regular.woff2")
        format("woff2");
      /* font-weight: normal;
        font-style: normal; */
    }

    body {
      font-family: "Pretendard-Regular";
    }

    h1,
    h2,
    h3,
    h4,
    h5,
    h6,
    header {
      font-family: "PartialSansKR-Regular";
    }
    ```

  - 부트스트랩
    https://getbootstrap.com/
    https://getbootstrap.com/docs/5.3/getting-started/introduction/#quick-start

  ```bash
  git switch main
  git merge step1
  # step1을 알아서 rebase하고 main 합치거나
  # main 합치면서 rebase하거나...
  # 그냥 merge
  # esc, :wq
  git push # release
  ```

- **STEP2** : Express, LLM, Glitch

  - Express + LLM

    - 배포한 웹 프로젝트와 같은 경로면 안됨! git이 겹치면 안돼요…

    ```bash
    git init
    npm init -y
    npm i express
    git add .
    git commit -m "big mistake" # node_modules가 포함됨
    # gitignore를 넣는다고 해서 한 번 커밋된게 자동으로 제거되진 않음
    # 보안 관련된 이슈는 git reset으로 커밋 자체를 밀어버려야해...
    # 파일이 포함된 건 이게 필수적임
    git rm -r --cached .
    git add .
    git commit -m "reset"
    ```

    ```
    node_modules
    package-lock.json
    ```

    **package.json**

    ```json
    {
      "name": "my-llm-wrapper",
      "version": "1.0.0",
      "main": "index.js",
      "scripts": {
        "start": "node server.js"
      },
      "keywords": [],
      "author": "",
      "license": "ISC",
      "description": "",
      "dependencies": {
        "express": "^4.21.2"
      }
    }
    ```

    ```bash
    npm i cors axios
    npm i -D nodemon
    ```

    ```json
    {
      "name": "my-llm-wrapper",
      "version": "1.0.0",
      "main": "index.js",
      "scripts": {
        "start": "node server.js",
        "test": "nodemon server.js"
      },
      "keywords": [],
      "author": "",
      "license": "ISC",
      "description": "",
      "dependencies": {
        "axios": "^1.7.9",
        "cors": "^2.8.5",
        "express": "^4.21.2"
      },
      "devDependencies": {
        "nodemon": "^3.1.9"
      }
    }
    ```

    터미널 `npm test`
    -> `127.0.0.1:3000`

    ```jsx
    // https://expressjs.com/
    // https://expressjs.com/en/resources/middleware/cors.html

    const express = require("express");
    const cors = require("cors");

    const app = express();
    const port = 3000;

    app.use(cors()); // 미들웨어
    // 모두에게 오픈.

    app.get("/", (req, res) => {
      //   res.send("Hello World!");
      res.send("Bye Earth!");
      // 수정 후 자동으로 리빌드 되는 건 자연스러운게 아님
      // 무언가 툴들이 도는 거에요... 여기선 nodemon
    });

    app.listen(port, () => {
      console.log(`app listening on port ${port}`);
    });
    ```

    ```jsx
    async function main() {
      async function hanldeCC() {
        // cors 때문에 (port가 달라서) 오류 나는 코드 -> CORS를 통해 해결
        document.querySelector("#box").textContent = await (
          await fetch("http://127.0.0.1:3000")
        ).text();
      }

      document.querySelector("#ccBtn").addEventListener("click", hanldeCC);
    }

    document.addEventListener("DOMContentLoaded", main);
    ```

    ***

    ```jsx
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>AI 맛집 추천</title>
        <link
          rel="icon"
          type="image/png"
          href="./assets/favicon-96x96.png"
          sizes="96x96"
        />
        <link rel="icon" type="image/svg+xml" href="./assets/favicon.svg" />
        <link rel="shortcut icon" href="./assets/favicon.ico" />
        <link
          rel="apple-touch-icon"
          sizes="180x180"
          href="./assets/apple-touch-icon.png"
        />
        <link rel="manifest" href="./assets/site.webmanifest" />
        <meta property="og:title" content="맛집 추천: 런치펀치" />
        <meta
          property="og:description"
          content="맛집 추천: 런치펀치는 전국 각지의 맛집을 소개하는 웹사이트입니다. 다양한 지역의 맛집을 한눈에 볼 수 있으며, 상세한 정보와 사진을 확인할 수 있습니다. 맛집을 찾을 때는 필수로 참고하는 사이트입니다."
        />
        <meta
          property="og:image"
          content="https://zero-aqua-coke.github.io/my-llm-pjt/assets/preview.png"
        />
        <meta
          property="og:url"
          content="https://zero-aqua-coke.github.io/my-llm-pjt/"
        />
        <meta property="og:type" content="website" />
        <link
          href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
          rel="stylesheet"
          integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
          crossorigin="anonymous"
        />
        <link rel="stylesheet" href="style.css" />
      </head>
      <body>
        <main>
          <section class="container mt-4">
            <h1>맛집 추천</h1>
            <p>맛집을 추천합니다</p>
            <section id="box"></section>
            <form id="ccForm">
              <input type="text" name="text" />
              <!-- <button id="ccBtn">추천 받기</button> -->
              <button>추천 받기</button>
            </form>
          </section>
        </main>
        <script
          src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
          integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
          crossorigin="anonymous"
        ></script>
        <script src="app.js"></script>
      </body>
    </html>
    ```

    ```jsx
    async function main() {
      async function hanldeCC(event) {
        event.preventDefault(); // Form의 기본 submit 막아줘야하고...
        const url = "http://127.0.0.1:3000";
        const formData = new FormData(document.querySelector("#ccForm"));
        const text = formData.get("text");
        // console.log(text);
        const response = await fetch(url, {
          method: "POST",
          body: JSON.stringify({
            text,
          }),
          headers: {
            "Content-Type": "Application/json",
          },
        });
        const json = await response.json();

        document.querySelector("#box").textContent = JSON.stringify(json);
      }

      //   document.querySelector("#ccBtn").addEventListener("click", hanldeCC);
      document.querySelector("#ccForm").addEventListener("submit", hanldeCC);
    }

    document.addEventListener("DOMContentLoaded", main);
    ```

    ```jsx
    // https://expressjs.com/
    // https://expressjs.com/en/resources/middleware/cors.html

    const express = require("express");
    const cors = require("cors");

    const app = express();
    const port = 3000;

    app.use(cors()); // 미들웨어
    // 모두에게 오픈.

    app.use(express.json()); // JSON으로 들어오는 body를 인식

    app.get("/", (req, res) => {
      //   res.send("Hello World!");
      res.send("Bye Earth!");
      // 수정 후 자동으로 리빌드 되는 건 자연스러운게 아님
      // 무언가 툴들이 도는 거에요... 여기선 nodemon
    });

    app.post("/", (req, res) => {
      const { body } = req;
      const { text } = body;
      res.json({ text });
    });

    app.listen(port, () => {
      console.log(`app listening on port ${port}`);
    });
    ```

    ```bash
    # ctrl + c
    npm i dotenv
    # .env
    # require("dotenv").config();
    ```

    ```bash
    # .gitignore .env
    node_modules
    package-lock.json
    .env
    ```

    ```bash
    # .env
    # https://console.groq.com/keys
    GROQ_API_KEY=
    # https://api.together.ai/settings/api-keys
    TOGETHER_API_KEY=
    ```

  - https://github.com/zero-aqua-coke/my-llm-wraper.git
  - Glitch -> `import from GitHub`
  - `public repo`를 끌어올 수 있다! → `.env`
  - `package.json`

```
{
  "name": "my-llm-wrapper",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "test": "nodemon server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "dependencies": {
    "axios": "^1.7.9",
    "cors": "^2.8.5",
    "dotenv": "^16.4.7",
    "express": "^4.21.2"
  },
  "engines": {
    "node": "14.x"
  },
  "devDependencies": {
    "nodemon": "^3.1.9"
  }
}
```

```
app.use(
  cors({
    origin: "https://zero-aqua-coke.github.io", // 여러분들 거
    methods: ["POST"],
    allowedHeaders: ["Content-Type"],
  })
);
```
