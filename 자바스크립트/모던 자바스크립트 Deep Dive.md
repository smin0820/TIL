📌모던 자바스크립트 Deep Dive
===

졸업 전까지 2~3회독을 목표로 하고있으며 이해한 부분은 내 언어로 잘 정리해서 기록하고 공부할 계획이다.

# ❓모든 값이 데이터 타입이 필요한 이유는?
1. 값을 저장할 때 확보해야 하는 **메모리 공간의 크기**를 결정하기 위해
2. 값을 참조할 때 한 번에 읽을 **메모리 공간의 크기**를 결정하기 위해
3. 메모리에서 읽어 들인 **2진수를 어떻게 해석**할지 결정하기 위해

<br>

# ✨지수 연산자
```javascript
2 ** 2 // 4
2 ** 0 // 1
2 ** -2 // 0.25

// 이항 연산자 중에서 우선순위가 가장 높다
2 * 5 ** 2 // 50
```

<br>

# ✨string.prototype.indexOf 메서드
```javascript
const string = 'hello world!';
const search = '!';
console.log(string.indexOf(search)) // 11
```
<br>

# ✨'1' > 0 // true
자바스크립트 엔진은 비교 연산자 표현식을 평가하기 위해 => 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적으로 타입을 변환 한다.

<br>

# ✨parseInt, parsefloat 함수
문자열 타입 => 숫자 타입만 가능<br>
```javascript
parseInt('2');  // 2
parseFloat('10.54');  // 10.54
```

<br>

# ✨단축 평가 논리곱(&&) 논리합(||)
```javascript
'Cat' || 'Dog' // 'Cat'
false || 'Dog' // 'Dog'
'Cat' || false // 'Cat'

'Cat' && 'Dog' // 'Dog'
false && 'Dog' // false
'Cat' && false // false
```

<br>

# ✨옵셔널 체이닝 연산자 : ?.
ES11(2020)에서 도입된 옵셔널 체이닝 연산자이다. 좌항 피연산자가 null 또는 undefined인 경우 undefined 반환하고 그렇지 않으면 우항 프로퍼티 참조한다.
```javascript
var a = null;

var value = a?.value;
console.log(value);  // undefined
```

<br>

# ✨null 병합 연산자 : ??
ES11(2020)에서 도입된 null 병합 연산자이다. 좌항의 피연산자가 null 또는 undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자 반환한다.
```javascript
var a = null ?? 'abc';
console.log(a);  // 'abc'
```