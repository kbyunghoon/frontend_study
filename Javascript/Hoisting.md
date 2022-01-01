<p align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/1200px-Unofficial_JavaScript_logo_2.svg.png" width="400px" />
</p>

# 호이스팅이란?
일단 호이스팅을 알기 위해서는 스코프, 함수 표현식과 함수 선언문을 알아 놓는 것이 좋다.

### 함수 선언문
```javascript
function a() {
  // 로직
}
```
일반적인 프로그래밍 함수 선언과 비슷하게 function으로 시작 되는 것이 함수 선언문이다.

### 함수 표현식
```javascript
const x = function () {
  // 익명 함수 표현식
}

const y = function a() {
  // 기명 함수 표현식
}
```
변수 값에 함수 표현을 담아 놓은 형태가 함수 표현식이다.
간단히 말하면 **정의한 함수를 값으로 변수에 할당한 것**이라고 보면 된다.

익명 함수 표현식은 함수에 **식별자가 주어지지 않으며**
기명 함수 표현식은 함수의 **식별자가 존재**한다.

## var, let const
개발자라면 var, let, const 키워드는 알 것이다.
### var 특징
- 함수 레벨 스코프
- 재선언 가능
- var 키워드 생략 가능

### let 특징
- 블록 수준 스코프
- 재선언 불가능
- let 키워드 생략 불가능

### const 특징
- 블록 수준 스코프
- 초기화와 동시에 선언이 이뤄져야 함
- 상수를 선언할 때 사용

# 호이스팅
호이스팅은 **변수의 선언을 최상단으로 끌어올려지는 현상**이다.

```javascript
console.log(name)
var name = "hoon"
```
위 코드를 콘솔에 찍어보면 에러가 나지 않고 'undefined'가 출력이 된다. 그 이유는 var 변수가 하단 코드처럼 회상단으로 끌어올려지기 때문이다.

```javascript
var name;
console.log(name)
name = "hoon"
```

일부 포스트에서는 let / const 함수 표현식은 호이스팅이 되지 않는다고 되어있다.
하지만 호이스팅이 되지 않는 것이 아니다.

```javascript
console.log(name)
let a = "hoon"
```
위 코드를 찍어보면 "a is not defined"를 출력한다.

```javascript
var a = "hoon"
{
  console.log(a)
  let a = "hoon"
}
```
위 코드는 "Cannot access 'a' before initialization"가 뜰 것이다.
그 이유는 '변수 라이프 사이클'의 초기화 단계 이전에 엑세스 할 수 없다는 에러가 출력된 것이다.
그 말은 호이스팅이 되었다는 말이다.
변수 라이프 사이클에 대해서는 하단을 확인하면 된다.

## 변수 라이프 사이클
### 1. 선언 단계 (Declaration phase)
변수 객체와 스코프가 생성되며, 스코프가 변수 객체를 참조.
### 2. 초기화 단계 (Initialization phase)
변수 객체 값을 위한 공간을 메모리에 할당.
### 3. 할당 단계 (Assignment phase)
변수 객체에 값을 할당

### 요약
1. 호이스팅은 **정의한 함수를 값으로 변수에 할당한 것**
2. var, let const 모두 호이스팅이 된다.