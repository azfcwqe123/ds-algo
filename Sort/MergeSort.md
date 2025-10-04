# Merge Sort (합병 정렬)

[그림]

![MergeSort01](https://github.com/user-attachments/assets/b63a39cf-33d8-4f59-bb01-c84847ac7a5f)

---

[코드]

```java
public class Merge_Sort {

    private static int[] sorted; // 추가 공간이 필요
    public static void main(String[] args) {
        
        int[] arr = new int[10];

        System.out.println("1부터 100까지의 난수 10개를 생성합니다.\n");

        for(int i = 0; i < 10; i++) { // 10개의 난수 생성
            arr[i] = (int) (Math.random() * 100) + 1;
        }

        System.out.println("정렬 전 배열의 상태 출력");
        printArr(arr); 
        
        mergeSort(arr); // 합병 정렬

        System.out.println("정렬 후 배열의 상태 출력");
        printArr(arr);

    }

    // 합병 정렬
    private static void mergeSort(int[] arr) {
        sorted = new int[arr.length];
        divide(arr, 0, arr.length - 1);
    }

    // 분할 작업
    private static void divide(int[] arr, int left, int right) {

        if(left == right) return; // 더 이상 쪼갤 수 없는 경우

        int mid = (left + right) / 2;

        divide(arr, left, mid);
        divide(arr, mid + 1, right);

        conquer(arr, left, mid, right); // 병합 작업
    }

    // 병합 작업
    private static void conquer(int[] arr, int left, int mid, int right) {
        int lt = left;
        int rt = mid + 1;
        int idx = lt;

        // 분할된 리스트의 합병
        while(lt <= mid && rt <= right) {
            if(arr[lt] <= arr[rt]) 
                sorted[idx++] = arr[lt++];
            else 
                sorted[idx++] = arr[rt++];                
        }

        // 오른쪽 리스트가 남았을 경우
        if(lt > mid) {
            while(rt <= right) sorted[idx++] = arr[rt++];
        }

        // 왼쪽 리스트가 남았을 경우
        else {
            while(lt <= mid) sorted[idx++] = arr[lt++];
        }

        // 정렬된 새 배열을 기존 배열에 복사
        for(int i=left; i<=right; i++) {
            arr[i] = sorted[i];
        }
    }

    private static void printArr(int[] arr) {
        for (int x : arr) {
            System.out.print(x + " ");
        }
        System.out.println("\n");
    }
}
```

결과1

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
80 50 67 15 7 90 49 53 83 39 

정렬 후 배열의 상태 출력
7 15 39 49 50 53 67 80 83 90
```

결과2

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
20 88 8 58 30 69 48 8 36 63

정렬 후 배열의 상태 출력
8 8 20 30 36 48 58 63 69 88
```

---


### 병합 정렬의 장점 & 단점

#### [장점]

1. **항상 O(N log N)의 시간 복잡도**

- 최선, 평균, 최악의 경우 모두 O(N log N)으로 일정

- 분할(나누기)과 병합(합치기)을 로그 단계로 반복하기 때문

&nbsp;

2. **안정 정렬이 보장됨**

- 같은 값을 가진 원소들의 상대적인 순서가 유지됨

- ex) 나이순으로 정렬할 때, 같은 나이의 사람들은 입력 순서가 보존됨

&nbsp;

3. **대용량 데이터에도 효율적**

- 정렬 과정에서 비교와 병합만 수행하기 때문에, 큰 배열에서도 성능이 일정하게 유지됨

 &nbsp;

#### [단점]

1. **추가 메모리 공간 필요**

- 정렬 과정에서 임시 배열(sorted[])을 사용하므로, **O(N)**의 추가 공간이 필요

2. **작은 데이터에서는 비효율적**

- 분할과 병합 과정의 오버헤드가 있기 때문에, 데이터 크기가 작을 경우 삽입 정렬보다 느림

---

### [병합 정렬 참고 영상]

https://www.youtube.com/watch?v=ZRPoEKHXTJg