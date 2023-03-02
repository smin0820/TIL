📌로컬에서 CORS policy 에러 원인과 해결 방법
====

![에러1](/img/CORS_에러/에러1.png)

로컬에서 토이 프로젝트를 만들다가 `type='module'`를 추가했더니 아래와 같은 에러가 발생했다.

![에러2](/img/CORS_에러/에러2.png)

# ❓원인
`type`이 `module`로 설정이된 `<script>`태그가 포함이된 HTML파일이 로컬에서 로드가될 경우 자바스크립트 모듈 보안 요구사항으로 인해 CORS 에러가 발생한다고 한다.

✏️**CORS**란?

Cross Origin Resource Sharing

✏️**CORS**의 목적

사용자의 데이터를 보호하기 위해 존재하며 이상한 출처의 리소스로 보내는 HTTP 및 HTTPS 요청을 제한하기 위해서다.

# ✨해결 방법 (2 가지)
1. 서버에 올리는 방법

    1. 터미널에서 http-server가 없으면 먼저 전역에 설치해 준다.
    ```
    npm install http-server -g
    ```

    2. http-server를 실행시켜 해당 폴더를 서버에 올려준다
    ```
    npx http-server
    ```

    3. 아래 URL로 접속
    ```
    http://127.0.0.1:8080
    ```

    4. 포트를 8080이 아닌 다른 포트로 실행하고 싶으면 원하는 포트로 접속
    ```
    npx http-server -p 원하는 포트번호
    ```



2. CORS 사용 체크 안 하는 방법

    1. chrome 속성 클릭
    ![에러3](/img/CORS_에러/에러3.png)

    2. 아래 문구를 복사해서 대상 뒤에 붙여준다.
    ```
     --disable-web-security --disable-web-security --user-data-dir=%LOCALAPPDATA%\Google\chromeTemp -–allow-file-access-from-files
    ```

    **--disable-web-security : CORS 사용 체크 안 함.**
    
    **-–allow-file-access-from-files : AJAX / JSON 같은 것을 사용 할 때 로컬 파일에 대한 엑세스 허용.**

    3. 그리고 chrome을 다시 관리자권한으로 실행해서 HTML 파일을 로드하면 해결!

# 참고 자료
https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F

https://velog.io/@takeknowledge/%EB%A1%9C%EC%BB%AC%EC%97%90%EC%84%9C-CORS-policy-%EA%B4%80%EB%A0%A8-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0-3gk4gyhreu

https://bongra.tistory.com/143

https://i5i5.tistory.com/935

https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy#Cross-origin_%EB%8D%B0%EC%9D%B4%ED%84%B0_%EC%A0%80%EC%9E%A5%EC%86%8C_%EC%A0%91%EA%B7%BC