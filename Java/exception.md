# Exception



### CheckedException / UnCheckedException

→ 개발자들이 만든 application code에서 예외가 발생했을 경우 사용한다.

**차이점 : UnCheckedException은 RuntimeException을 상속한다.**

![Exception%20cc212ee4806a44e2993d46cc7b7b39c5/Untitled.png](Exception%20cc212ee4806a44e2993d46cc7b7b39c5/Untitled.png)

CheckedException은 이미 개발자가 exception에 대한 대처를 했을 것으로 예상하여 Rollback이 안되므로, 복구 전략을 가져야 한다.



### CheckedException

컴파일 시간에 검사하는 예외이다. 처리하지 않는다면 compile error가 발생한다. 1.try-catch로 감싸거나, 2.throws로 호출한 메서드들에게 예외를 넘겨준다. 개발자가 처리했을 것 이라고 예상하여 rollback이 불가능하다. 

### UncheckedException

런타임에 검사하는 error. 컴파일하는데 문제는 없지만, 실행 중에 예외가 발생할 수 있다. Rollback이 가능하다.

StackTrace - 보다 더 자세하게 예외가 발생한 부분을 추적 가능한 지표이다.