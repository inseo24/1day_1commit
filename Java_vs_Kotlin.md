### 자바와 코틀린의 차이점

**차이점 1**

코틀린에서는 `fun` 같은 키워드를 사용함. 키워드니까 당연히 식별자로 사용할 수 없을 것 같지만, 또 역따옴표로 감싸면 허용된다.

*이유*: 자바에서는 그걸 식별자로 사용할 수 있는데, 코틀린에서 자바에서 정의한 식별자를 가져와 사용해야 할 때가 있을 수 있기 때문입니다.

```kotlin
val i1_ = "test"
println(i1_)

val import = "ok"
// val val = "x"

/*
    * fun 같은 키워드는 자바에선 사용되지 않으나, 코틀린에서는 키워드로 사용함
    * 그러다 보니 자바에선 식별자로 사용 가능한데, 코틀린에서는 사용할 수 없어서 역따옴표(`)로 감싸서 식별자 사용을 허용함
    *
    * 그럼 역따옴표 감싸서 쓰는 건 왜 허용했냐
    * 1. 코틀린에서 자바에서 정의한 식별자를 사용해야 하는 경우가 있을 수 있어서 허용
    * 2. 테스트케이스에서 메서드 이름 쓸 때 유용함
    * @Test fun `2 + 2 should be 4`() { (2 + 2) shouldBe 4 }
    *
    * */
val `fun` = "ok"
//        val fun = "x"

println(`fun`)
```

**차이점 2**

자바에선 `=`(assignment)이 식(expression)임. 그런데 코틀린에서 `=`은 문(statement)임, 아무 값도 돌려주지 않음.

*이유*: 쓰다가 실수하기 쉬우니 이런 대입을 금지하자 뭐 이런 이유 같음 그리고 실제로 쓸 일도 별로 없지 않냐(?)

```kotlin
var a: Int
var b: Int
var c: Int

/*
* 연쇄 대입 불가능
* Assignments are not expressions, and only expressions are allowed in this context
*/
//  a = b = c
```

**차이점 3**

자바에선 unreachable code가 오류인데 코틀린은 아님. 그냥 컴파일러에서 경고를 표시하고 IDE에서 알려줘서 죽은 코드인 걸 확인할 수 있긴 함

**차이점 4**

코틀린엔 checked, unchecked exception을 구분하지 않음. 코틀린에선 모든 예외가 unchecked exception 임.

*이유*: 자바에서 checked exception일 때 예외 처리를 강제하는 것이 코틀린에선 없음. 런타임 예외로 충분하지 않냐는 것 같음.

**차이점 5**

코틀린에서 함수 파라미터는 불변임. 자바는 디폴트가 가변이라 함수 내부에서 변경 못 하게 하려면 `final`로 지정해야 함.

```java
// java는 가변이 디폴트
    public int increment(int num) {
        return num++;
    }

    public void test() {

        var result = increment(3);
    }
```

```kotlin
/*
*
* 코틀린은 함수 파라미터가 무조건 불변임. 아래 코드는 에러
* */
fun increment(n: Int): Int {

//            return n++

}
```

**차이점 6**

`import static` directive가 코틀린엔 없음. 코틀린의 모든 선언은 일반적인 `import` directive 구문을 사용해 임포트를 함. 자바에서 보던 `import static ...`이 없고 모든 선언이 `import`를 사용한다고 보면 됨.

```java
import static com.example.demo.MainApplication.main; // ok
```

```kotlin
import com.example.demo.DemoApplication.Companion.test
```
