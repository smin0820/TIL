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

<br>

# ✨스택 오버플로(stack overflow) 에러
재귀함수는 자신을 무한 재귀 호출한다고 한다. 따라서 함수 내에서 재귀 호출을 멈출 수 있는 **탈출 조건**을 반드시 만들어야 한다. 예를 들어서, 1이하 일 때 호출을 멈춘다. 이처럼 탈출 조건이 없으면 무한 스택 오버플로 에러가 발생한다.

    여기서 스택 오버플로 란?
        - stack 영역의 메모리가 지정된 범위를 넘엄갈 때 발생한다.
    
Stack 메모리는 보통 지역 변수가 저장되는 영역이다. 함수에서 지역 변수를 선언하면 지역 변수는 Stack 메모리에 할당되고 함수를 빠져나오면 Stack 메모리에서 해제된다.

하나의 프로그램이 실행될 때 수많은 함수를 호출하고 빠져 나오게 되는데 그 때마다 함수에서 사용하는 지역 변수는 Stack 영역에 할당되고 해제되는 것을 반복하게 되며 그에 따라 사용하는 Stack 영역도 변하게 된다.
    
만약 한 함수에서 너무 큰 지역 변수를 선언하거나 함수를 재귀적으로 무한정 호출하게 되면 stack overflow가 발생할 수 있다.

stack overflow가 발생하면 컴파일러 옵션에서 stack 영역의 크기를 늘리거나 또는 함수에서 사용하는 지역 변수의 크기를 줄이거나 아니면 지역 변수를 전역 변수로 바꾸어 해결할 수 있다.


# ✨고차함수와 콜백함수
```js
// 고차함수 : 매캐변수를 통해 함수의 외부에서 콜백 함수를 전달받은 함수
function repeat(n, f) {
    for(var i = 0; i < n; i++) {
        f(i);
    }
}
// 콜백함수 : 함수의 매개변수를 통해 함수의 내부로 전달되는 함수
var logAll = function(i) {
    console.log(i);
};

repeat(5, logAll);
```