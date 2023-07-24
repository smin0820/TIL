# ✨ var
### 1> 변수 중복 선언 허용
- var 키워드로 선언된 변수는 같은 스코프 내에서 중복 선언 허용한다.
- 초기화문이 없는 변수 선언문은 무시된다.

```js
var x = 1;
var y = 1;

var x = 100;
var y;

console.log(x);         // 100
console.log(y);         // 1
```

### 2> 함수 레벨 스코프
- 함수 외부에서 var 키워드로 선언하고, 함수 내부/코드 블록 내에서 선언해도 전역 변수가 된다.
```js
var x = 1;

if(true) {
	var x = 10;
}

console.log(x);		  // 10
```

- for문에서 선언한 i는 전역 변수이며, 이미 선언된 변수라서 중복 선언된다.
```js
var i = 10;

for(var i = 0; i < 5; i++) {
	console.log(x);        // 0 1 2 3 4    	 
}

console.log(x);            // 10
```

### 3> 변수 호이스팅
- (변수 호이스팅) var 키워드로 선언한 변수는 변수 선언문 이전에 참조 가능.
- 할당문 이전에 참조하면 undefined를 반환한다.

```js
console.log(min);          // undefined

min = 98;

console.log(min);          // 98

var min;
```

<br>

# ✨ let
### 1> 변수 중복 선언 금지
- let 키워드는 이름이 같은 변수를 중복 선언하면 문법 에러가 발생한다.

### 2> 블록 레벨 스코프
- 함수 내의 코드는 함수 레벨 스코프를 따르고, for문 내에서는 블록 레벨 스코프를 따른다.
```js
let i = 10;

function foo() {
 let i = 100;
  
  for(let i = 1; i < 3; i++) {
  	console.log(i);                // 1 2  
  }
 console.log(i);                   // 100
}

foo();

console.log(i);                    // 10
```

### 3> 변수 호이스팅
- let 키워드로 선언한 변수를 변수 선언문 이전에 참조하면 참조에러 발생.
```js
console.log(min);                  // ReferenceError: min is not defined

let min;
console.log(min);                  // undefined

min = 24;
console.log(min);                  // 24

```

<br>

# ✨ const

### 1> 선언과 동시에 초기화
- const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다.

### 2> 블록 레벨 스코프
- let 키워드와 마찬가지로 블록 레벨 스코프를 가지며, 변수 호이스팅이 발생하지 않는 것처럼 보인다.
```js
{
	console.log(min);              // ReferenceError
	const min = 24;
  	console.log(min);              // 24    
}

console.log(min);                  // ReferenceError: min is not defined
```


### 3> 재할당 금지 + 값 변경 불가
- var, let 키워드와 다르게 const로 선언한 변수는 재할당이 금지된다.
- 그래서 코드의 가독성과 유지보수를 위해 적극적으로 사용하는 것이 좋다.

```js
const coupon = 0.2;

let water = 1000;
let coke = 1500;

let price = (water + coke) * (1 - coupon);

console.log(price);
```

<br>

# 정리
- 변수 선언할 때 기본적으로 const를 사용하고, let은 재할당이 필요한 경우에 사용하는 것이 좋다.