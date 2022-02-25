# Function

```
//함수 선언식
function multiply(number) {
  return number * number;
}

//함수 표현식
let multiply = function(number){
  return number * number;
}
```

## 호이스팅(Hoisting)

함수 선언문의 경우, 함수 선언의 위치와는 상관없이 코드 내 어느곳에서든지 호출이 가능한데, 이것을 함수 호이스팅이라고 한다.

자바스크립트는 ES6의 let, const를 포함하여 모든 선언(var, let, const, function, function\*, class)을 호이스팅한다.

var, function등 모든 선언문이 해당 scope의 선두로 옮겨진 것처럼 동작하는 특성으로 모든 선언문이 선언되기 이전에 참조가 가능하다.

함수 선언문으로 정의된 함수는 자바스크립트 엔진이 스크립트가 로딩되는 시점에 바로 초기화 하고 이를 VO(Variable Object, 실행 컨텍스트 참조)에 저장하여 함수 선언, 초기화, 할당이 한번에 이루어진다.

함수 표현식의 경우 함수 호이스팅이 아니라 변수 호이스팅이 발생한다. 변수 호이스팅은 변수 생성 및 초기화와 할당이 분리되어 진행된다. 호이스팅 된 변수는 undefined으로 초기화 되고 실제값의 할당은 할당문에서 이루어진다. 함수 표현식은 스크립트 로딩 시점에 변수 객체에 함수를 할당하지 않고 runtime에 해석되고 실행되므로 이 두가지 구분이 중요하다.
