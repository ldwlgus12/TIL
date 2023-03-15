# # 04. JS-Functions

- 참조 자료형 (Reference type)
    - Objects (Object, Array, Function)

- Function : 참조 자료형에 속하며 모든 함수는 Function object

- 함수의 구조
    - 함수의 이름
    - 함수의 매개변수
    - 함수의 body를 구성하는 statement

```javascript
function name ([param [, param, [..., param]]]) {
    statements
    return value
}

- return이 없다면 undefined를 반환
```

<br>

## # 함수의 정의

- 선언식 (function declaration)
```javascript
function funcName () {
    statements
}

--------------------------------
예시)

function add (num1, num2) {
    return num1 + num2
}

console.log(add(3, 9))
```

<br>

- 표현식 (function expression)
```javascript
const funcName = function () {
    statements
}

--------------------------------
예시)

const sub = function (num1, num2) {
    return num1 - num2
}

console.log(sub(3, 9))
```

- 함수 표현식 특징
    - 함수 이름이 없는 '익명 함수'를 사용할 수 있음
    - 선언식과 달리 표현식으로 정의한 함수는 호이스팅 되지 않으므로 코드에서 나타나기 전에 먼저 사용할 수 없음
    - 사용 권장

<br>

- `기본 함수 매개변수` (Default function parameter)
    - 값이 없거나 undefined가 전달될 경우 이름 붙은 매개변수를 기본값으로 초기화

```javascript
const greeting = function (name = 'apple') {
    return `Hi ${name}`
}

console.log(greeting())  // Hi apple
```

<br>

- `매개변수와 인자의 개수 불일치`
```javascript
// 매개변수 개수 < 인자 개수
// 에러를 내지 않는다.
const noArgs = function () {
    return 0
}

console.log(noArgs(1,2,3))  // 0


const twoArgs = function (num1, num2) {
    return [num1, num2]
}

console.log(twoArgs(1,2,3))  // [1, 2]

--------------------------------

// 매개변수 개수 > 인자 개수
const threeArgs = function (num1, num2, num3) {
    return [num1, num2, num3]
}

console.log(threeArgs(1))  // [1, undefined, undefined]
```

<br>

- `나머지 매개변수` (Rest parameters)
    - 무한한 수의 인자를 '배열'로 허용하여 가변 함수를 나타내는 방법

```javascript
const myFunc = function (num1, num2, ...restArgs) {
    return [num1, num2, restArgs]
}

console.log(myFunc(1,2,3,4,5))  // [1, 2, Array(3) - [3, 4, 5]]
console.log(myFunc(1,2))  // [1, 2, Array(0) - []]


- 함수 정의에는 하나의 나머지 매개변수만 있을 수 있음
- 나머지 매개변수는 함수 정의에서 마지막 매개변수여야 함
```

<br>

- `화살표 함수 표현식` (Arrow function expressions)
    - 함수 표현식의 간결한 표현법

<br>

- 화살표 함수 표현식 작성 순서

1. function 키워드 제거 후 매개변수와 중괄호 사이에 화살표 (=>) 작성

2. 함수의 매개변수가 하나 뿐이라면 매개변수의 '()' 제거 가능

3. 함수 본문의 표현식이 한 줄이라면 '{}'와 'return' 제거 가능

```javascript
const greeting = function (name) {
    return `Hello, ${name}`
}

// 1. function 키워드 삭제 후 화살표 작성
// 1단계 까지는 자유자재로 쓸 수 있어야 함.
const arrow1 = (name) => {
    return `Hello, ${name}`
}


// 3. 함수 바디가 return을 포함한 표현식 1개일 경우에 {} & return 삭제 가능
const arrow2 = (name) => `hello, ${name}`
```


