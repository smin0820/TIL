๐๋ก์ปฌ์์ CORS policy ์๋ฌ ์์ธ๊ณผ ํด๊ฒฐ ๋ฐฉ๋ฒ
====

![์๋ฌ1](/img/CORS_์๋ฌ/์๋ฌ1.png)

๋ก์ปฌ์์ ํ ์ด ํ๋ก์ ํธ๋ฅผ ๋ง๋ค๋ค๊ฐ `type='module'`๋ฅผ ์ถ๊ฐํ๋๋ ์๋์ ๊ฐ์ ์๋ฌ๊ฐ ๋ฐ์ํ๋ค.

![์๋ฌ2](/img/CORS_์๋ฌ/์๋ฌ2.png)

# โ์์ธ
`type`์ด `module`๋ก ์ค์ ์ด๋ `<script>`ํ๊ทธ๊ฐ ํฌํจ์ด๋ HTMLํ์ผ์ด ๋ก์ปฌ์์ ๋ก๋๊ฐ๋  ๊ฒฝ์ฐ ์๋ฐ์คํฌ๋ฆฝํธ ๋ชจ๋ ๋ณด์ ์๊ตฌ์ฌํญ์ผ๋ก ์ธํด CORS ์๋ฌ๊ฐ ๋ฐ์ํ๋ค๊ณ  ํ๋ค.

โ๏ธ**CORS**๋?

Cross Origin Resource Sharing

โ๏ธ**CORS**์ ๋ชฉ์ 

์ฌ์ฉ์์ ๋ฐ์ดํฐ๋ฅผ ๋ณดํธํ๊ธฐ ์ํด ์กด์ฌํ๋ฉฐ ์ด์ํ ์ถ์ฒ์ ๋ฆฌ์์ค๋ก ๋ณด๋ด๋ HTTP ๋ฐ HTTPS ์์ฒญ์ ์ ํํ๊ธฐ ์ํด์๋ค.

# โจํด๊ฒฐ ๋ฐฉ๋ฒ (2 ๊ฐ์ง)
1. ์๋ฒ์ ์ฌ๋ฆฌ๋ ๋ฐฉ๋ฒ

    1. ํฐ๋ฏธ๋์์ http-server๊ฐ ์์ผ๋ฉด ๋จผ์  ์ ์ญ์ ์ค์นํด ์ค๋ค.
    ```
    npm install http-server -g
    ```

    2. http-server๋ฅผ ์คํ์์ผ ํด๋น ํด๋๋ฅผ ์๋ฒ์ ์ฌ๋ ค์ค๋ค
    ```
    npx http-server
    ```

    3. ์๋ URL๋ก ์ ์
    ```
    http://127.0.0.1:8080
    ```

    4. ํฌํธ๋ฅผ 8080์ด ์๋ ๋ค๋ฅธ ํฌํธ๋ก ์คํํ๊ณ  ์ถ์ผ๋ฉด ์ํ๋ ํฌํธ๋ก ์ ์
    ```
    npx http-server -p ์ํ๋ ํฌํธ๋ฒํธ
    ```



2. CORS ์ฌ์ฉ ์ฒดํฌ ์ ํ๋ ๋ฐฉ๋ฒ

    1. chrome ์์ฑ ํด๋ฆญ
    ![์๋ฌ3](/img/CORS_์๋ฌ/์๋ฌ3.png)

    2. ์๋ ๋ฌธ๊ตฌ๋ฅผ ๋ณต์ฌํด์ ๋์ ๋ค์ ๋ถ์ฌ์ค๋ค.
    ```
     --disable-web-security --disable-web-security --user-data-dir=%LOCALAPPDATA%\Google\chromeTemp -โallow-file-access-from-files
    ```

    **--disable-web-security : CORS ์ฌ์ฉ ์ฒดํฌ ์ ํจ.**
    
    **-โallow-file-access-from-files : AJAX / JSON ๊ฐ์ ๊ฒ์ ์ฌ์ฉ ํ  ๋ ๋ก์ปฌ ํ์ผ์ ๋ํ ์์ธ์ค ํ์ฉ.**

    3. ๊ทธ๋ฆฌ๊ณ  chrome์ ๋ค์ ๊ด๋ฆฌ์๊ถํ์ผ๋ก ์คํํด์ HTML ํ์ผ์ ๋ก๋ํ๋ฉด ํด๊ฒฐ!

# ์ฐธ๊ณ  ์๋ฃ
https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F

https://velog.io/@takeknowledge/%EB%A1%9C%EC%BB%AC%EC%97%90%EC%84%9C-CORS-policy-%EA%B4%80%EB%A0%A8-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0-3gk4gyhreu

https://bongra.tistory.com/143

https://i5i5.tistory.com/935

https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy#Cross-origin_%EB%8D%B0%EC%9D%B4%ED%84%B0_%EC%A0%80%EC%9E%A5%EC%86%8C_%EC%A0%91%EA%B7%BC