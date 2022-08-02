## bubble sort 문제 

```java
import java.util.*;

public class Solution {
    public int[] bubbleSort(int[] arr) {
        // 1. 첫 번째 요소가 두 번째 요소보다 크면, 두 요소의 위치를 바꿉니다.
        // 2. 두 번째 요소와 세 번째 요소보다 크면, 두 요소의 위치를 바꿉니다.
        // 3. 1, 2를 마지막까지 반복합니다. (마지막에서 두 번째 요소와 마지막 요소를 비교)

        // 4. 1~3의 과정을 한 번 거치게 되면, 가장 큰 요소가 배열의 마지막으로 밀려납니다.
        // 5. 1~3의 과정을 첫 요소부터 다시 반복합니다.

        // 6. 5를 통해 두 번째로 큰 요소가 배열의 마지막 바로 두 번째로 밀려납니다.
        // 7. 1~3의 과정을 총 n번(배열의 크기) 반복합니다.

        // 위에서 설명된 알고리즘 1~3의 과정 중 어떤 요소도 위치가 바뀌지 않은 경우, 배열이 정렬된 상태라는 것을 알 수 있습니다.


        for(int i=1; i<=arr.length; i++) {
            int[] array = Arrays.copyOf(arr, arr.length);
            bbs(arr);
            if(arr == array) break;
        }
        return arr;
    }
    static int[] bbs(int[] arr) {
        for (int i = 0; i < arr.length - 1; i++) {
            int a = arr[i];
            int b = arr[i + 1];
            if (arr[i] > arr[i + 1]) {
                arr[i] = b;
                arr[i + 1] = a;
            }
        }
        return arr;
    }
}
```

## 다시푼거
```java
import java.util.*;

public class Solution {
    public int[] bubbleSort(int[] arr) {
        for(int i=0; i<arr.length-1; i++) {
            int count = 0;
                for (int j = 0; j < arr.length - 1; j++) {
                    if (arr[j] > arr[j + 1]) {
                        swap(arr, j, j + 1);
                        count++;
                    }
                }
            if(count == 0) break;
        }
        return arr;
    }
    static int[] swap(int[] arr, int one, int two) {
        int a = arr[one];
        int b = arr[two];
        arr[one] = b;
        arr[two] = a;
        return arr;
    }
}
```
 ### 실행시간 초과 나옴 내일 다시 (6/24)
 ### Arrays.copyOf가 시간이 오래걸린거 같음. 위치를 바꾸기만 하는 메서드로 변경 후 메서드 실행 횟수를 체크하는 방식으로 품
