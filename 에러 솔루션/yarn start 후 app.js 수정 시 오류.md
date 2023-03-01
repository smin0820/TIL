📌yarn start 후 app.js 수정 시 오류
=====

1. 터미널에서 yarn start를 입력하고
2. app.js 파일을 수정한 후 저장하면

아래와 같은 오류가 발생한다.
![오류1](/img/yarn_start_오류/오류1.png)

# ❓원인
에러가 발생하는 이유는 create react-app과 yarn에서 충돌이 발생하기 때문이다. 그래서 eslint관련해서 수동적으로 설정 해야한다.

<br>

# ✨해결 방법
1. 우선 yarn을 중지한다.
![오류2](/img/yarn_start_오류/오류2.png)

<br>

2. yarn add -D eslint-config-react-app 추가
![오류3](/img/yarn_start_오류/오류3.png)

<br>

3. 터미널에서 다시 한번 `yarn start` 하고, App.js를 수정했을때 아래와 같은 오류가 발생하면
![오류4](/img/yarn_start_오류/오류4.png)

<br>

4. 폴더 가장 상단에 .yarnrc.yml 파일 추가
![오류5](/img/yarn_start_오류/오류5.png)

<br>

5. `.yarnrc.yml` 파일에 그대로 작성
![오류6](/img/yarn_start_오류/오류6.png)

<br>

6. 터미널에 순서대로 `yarn cache clean`, `yarn install`, `yarn start` 입력

<br>

7. 완료!


# 참고 자료
https://velog.io/@bishoe01/Yarn-create-react-app-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EC%98%A4%EB%A5%98%ED%95%B4%EA%B2%B0%EB%B0%A9%EB%B2%95