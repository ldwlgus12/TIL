# # 05. JS-Object

- (plain) `Object` : 키로 구분된 데이터 집합 (data collection)을 저장하는 자료형

- 객체의 구조
    - 중괄호를 이용해 작성
    - 중괄호 안에는 key: value 쌍으로 구성된 속성 (property)를 여러 개 넣을 수 있음
    - key는 문자형, value는 모든 자료형이 허용
```javascript
const user = {
    name: 'sophia',
    age: 30,
    'key with space': true,
}


- true 옆 , : 'trailing comma' - 속성을 추가, 삭제, 이동하기가 용이해짐
```

<br>

## # 객체의 속성
- Property 활용
```javascript
//조회 (점 표기법, 대괄호 표기법)
console.log(user.age)
console.log(user['age'])
console.log(user['key with space'])

// 추가
user.address = 'korea'
console.log(user)

// 수정
user.age = 40
console.log(user)

// 삭제
delete user.address
console.log(user)
```
<br>

- Property 존재 여부 확인 - `in`
```javascript
// in 연산자
console.log('age' in user)
console.log('country' in user)
```
<br>

- 단축 Property
    - 키 이름과 값으로 쓰이는 변수의 이름이 같은 경우 단축 구문을 사용할 수 있음
```javascript
// 단축 속성
const age = 30
const address = 'korea'

const oldUser = {
    age: 'age',
    address: 'address',
}

const newUser = {
    age,
    address,
}
```
<br>

- 계산된 Property
    - 키가 대괄호(`[]`)로 둘러싸여 있는 프로퍼티
    - 고정된 값이 아닌 변수 값을 사용할 수 있음
```javascript
// 계산된 속성
const product = prompt('물건 이름을 입력해주세요.')
const a = 'my'
const b = 'property'

// 변수 값에 따라 key 값이 변화
const bag = {
    [product]: 5,
    [a + b]: true,
}

console.log(bag)  // {연필: 5, myproperty: 'value'}
```

<br>

## # 객체와 함수
- `Method` : 객체 속성에 정의된 함수
- Method 예시
    - object.method() : 메서드는 객체를 `행동`할 수 있게 함

```javascript
const person = {
    name: 'sophia',
    greeting: function () {
        return 'hello'
    },
}

//greeting 메서드 호출
console.log(person.greeting())  // Hello
```
<br>

- `'this' 키워드를 사용해 객체에 대한 특정한 작업을 수행 할 수 있음 `
```javascript
Method + this 예시)

const person1 = {
    name: 'sophia',
    greeting: function () {
        return `hello, ${this.name}`
        // 여기서 this는 person1 (본인을 '호출'하는 객체)
        // this 대신 person1을 쓰면 동작은 됨. 하지만 쓰면 안되는 이유는 상속이나, 중첩된 함수가 됐을 때 또 달라지기 때문이다. 
    },
}

console.log(person1.greeting())
// Hello, sophia
```
<br>

- 🌟`'this'` keyword
    - 함수나 메서드를 호출한 객체를 가리키는 키워드 (함수 내에서 객체의 속성 및 메서드에 접근하기 위해 사용)

- JS에서 this는 함수를 `호출하는 방법`에 따라 가리키는 대상이 다름
    - 단순 호출 시 -> 전역 객체
    - 메서드 호출 시 -> 메서드를 호출한 객체

```javascript
// 단순 호출 시
const myFunc = function () {
    return this
}

// 최상위 객체인 window가 호출됨. 항상 본인 객체를 호출하지 않음
console.log(myFunc())


// 메서드 정의 할 때 (this를 사용한다면) 화살표 함수 금지 (특히나 객체에서는)
// this를 사용 안하면 상관없음
```

<br>

## # 참고
- JavaScript 'this' 특징
    - JavaScript에서 this는 함수가 '호출되는 방식'에 따라 결정되는 현재 객체를 나타냄
    - Python의 self와 Java의 this는 선언 시 값이 이미 정해지는 것에 비해 JavaScript의 this는 함수가 호출되기 전까지 값이 할당되지 않고 호출 시에 결정됨 (동적)

- JSON (JavaScript Object Notation)
    - Key-value 형태로 이루어진 자료 표기법
    - JavaScript의 Object와 유사한 구조를 가지고 있지만 JSON은 형식이 있는 '문자열'
    - JavaScript에서 JSON을 사용하기 위해서는 Object 자료형으로 변경해야 함

    