조건에 따라 다른 실행을 해야 할 경우 사용하는 자바스크립트의 제어문에 대해서 알아봅니다.

## 1. if ~ else

if(....) 괄호 안에 들어가는 조건이 ```true```일 경우 코드가 실행 됩니다.

꼭 ```true```, ```false```를 명시적으로 적지 않아도 자동으로 [형변환](https://ko.javascript.info/type-conversions)이 일어납니다.

* 숫자 `0`, 빈 문자열`""`, `null`, `undefined`, `NaN`은 불린형으로 변환 시 모두 :point_right: `false`
* 이 외의 값은 불린형으로 변환시:point_right: `true`
* else 부분은 조건이 ```false```인 경우 실행 되는 코드입니다.

```js
// 코드 작성 예시

if (조건) {
  만약 조건(condition)이 참일 경우 실행할 코드
} else {
  대신 실행할 다른 코드
}
```



## 2. 삼항연산자(조건부 연산자 `?`)

if~else로 구현된 조건문을 조금 더 간결하고 짧게 코드로 표한 할 수 있습니다.

```js
//코드 작성 예시

var x = 100;
var y = 1;
var z
//if~else 작성시
if(x>y) {
    z = "x는 y보다 큽니다";
} else {
     z ="x는 y보다 작습니다."
}
console.log(z) // "x는 y보다 큽니다."

// condition(조건문) ? value if true(선택문 1) : value if false(선택문2)
var x = 100;
var y = 1;
var z = x > y ? "x는 y보다 큽니다" : "x는 y보다 작습니다."
console.log(z) // "x는 y보다 큽니다."
```

:exclamation:주의사항:exclamation:

조건 부분에 ```false```로 평가되는 값이 들어 오면 예상치 못한 결과를 얻을 수도 있다.

```js
const num = 0;
const result = num ? num : -1;

console.log(result) // -1; 0은 false로 판단되는 값이므로...
```

:heavy_plus_sign: null 병합연산자

* 형식 :  값1 ?? 값2

* 의미 :  값1이 null, undefined가 아닌 경우에만 값1을 반환

  ```js
  console.log(null ?? "null~") //null~
  console.log("안녕하세요 :)" ?? "null...") //"안녕하세요 :)"
  console.log(0 ?? "null이나 undefined가 아님") //0
  ```

:heavy_plus_sign: 옵션널 체이닝 연산자

* 형식 :  객체```?.```키

* 의미 : 왼쪽 객체가 null, undefined가 아닌경우에만, ```객체.키```값을 참조한다.

  ```js
  const obj = {
      name:"javascript",
      age : "100000",
  }
  
  console.log(obj?.name); // "javscript"
  console.log(obj?.first); // undefined
  console.log(obj.first); //Error 발생!!!
  ```

## 3. Switch

if ~ else if ~ else 문을 간결하게 표현 할 수 있는 문입니다.

* switch는 표현식의 평가 결과를 각 case 표현식의 값들과 매치하면서 내려갑니다.
* 맞는 case가 있다면 ```breake```를 만나기 전까지 코드를 실행합니다.
* default는 필수 사항은 아닙니다.
* default를 작성한다면  ```breake```는 꼭 써주어야 합니다.
* :star:switch표현식과 case 표현식 간의 매치는 ```===(엄격매치)```입니다!

```js
//코드 작성 예시

const num = 42;
switch(num) {
    case 2 :
        console.log("2입니다.");
        break;
    case 42 :
        console.log("42입니다.");
        break;
    default:
        console.log("아무것도 아닙니다.")
        break;
}

//switch엄격매치
const a = "Hello";
const b = 10;

switch(true) {
    case (a || b == 10) :  //👈엄격히 true가 아니므로 지나치게 된다
        console.log("yeah!")
        break;
   	default : 
        console.log("ㅠㅠ");
        break;
}
        
```

