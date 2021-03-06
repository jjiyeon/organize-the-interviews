# Promise 와 Callback의 차이

## Callback 방식의 비동기 처리가 갖는 문제점

자바스크립트에서 빈번하게 사용되는 비동기 처리 모델은 요청을 병렬로 처리하여 다른 요청이 블로킹 되지 않는 장점이 있다.
하지만 비동기 처리를 위한 콜백 패턴은 여러개를 중첩해서 사용했을 경우 콜백 헬이 발생된다는 단점이 있다. 콜백 헬은 비동기 함수의 처리 결과를 반환하는 경우, 순서를 보장할 수 없기 때문에 그 반환 결과로 후속 처리를 위해 콜백 함수 내에서 함수가 중첩되는 현상이다. 그로 인해 코드의 가독성이 나빠지고 복잡도가 높아진다.
또한, 에러처리가 곤란하다는 것인데, 아래의 경우에서 던져진 에러는 catch에서 잡지 못한다.

```
try {
  setTimeout(() => { throw new Error('Error!'); }, 1000);
} catch (e) {
  console.log('에러를 캐치하지 못한다..');
  console.log(e);
}
```

그 이유는, 비동기 콜백 함수에서 setTimeout의 이벤트(timer함수의 tick 이벤트) 경우 태스크 큐(Task Queue)로 이동한 후 호출 스택(Call Stack)이 비어졌을 때, 호출 스택으로 이동되어 실행되기 때문이다. setTimeout 함수는 이미 호출스택에서 실행되고 종료되어 이미 빠져나간 후 이기 때문에, 호출 스택에서 실행 될때는 호출한 곳은 setTimeout이 아니기 때문에 에러는 catch 되지 않고 프로세스는 종료된다.
이런 문제를 극복하기 위해 Promise가 제안되었다.

## Promise

Promise는 비동기 처리가 성공(fulfilled) 하였는지, 실패(rejected)하였는지 등 상태를 갖는다. 후속처리 메소드(then, catch, finally) 사용으로 비동기 처리에서 발생하는 에러와, 후속처리 메소드의 에러 모두를 잡을 수 있다.
