### 9655

- 간단함. 돌은 1개 또는 3개만 가져갈 수 있으니, 먼저 가져가는 사람은 돌의 개수가 홀수면 항상 마지막 돌을 가져감.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int N = scanner.nextInt();
        
        if (N % 2 == 0) {
            System.out.println("CY");
        } else {
            System.out.println("SK");
        }
    }
}
```


```kotlin
import java.util.Scanner

fun main(args: Array<String>) {
    val scanner = Scanner(System.`in`)
    val N = scanner.nextInt()
    
    if (N % 2 == 0) {
        println("CY")
    } else {
        println("SK")
    }
    
    scanner.close()
}
```
