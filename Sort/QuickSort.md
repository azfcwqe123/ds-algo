# Quick Sort (퀵 정렬)

[그림]

![QuickSort01](https://github.com/user-attachments/assets/7550b3ba-ddff-4758-8295-48b3d838a7eb)

![QuickSort02](https://github.com/user-attachments/assets/692a85bf-1dcd-40dd-b400-8ca008c257b7)

![QuickSort03](https://github.com/user-attachments/assets/ff7b35b8-1bb8-42fb-a138-a892fa683487)

![QuickSort04](https://github.com/user-attachments/assets/4fb4f4c5-dc7d-433d-9fb9-7bc6d57b07c8)

![QuickSort05](https://github.com/user-attachments/assets/cfc60163-3bfb-4f47-bedb-22e862525327)

![QuickSort06](https://github.com/user-attachments/assets/0bdc5757-9fc8-434c-816b-929527633f91)

---

[코드]

```java
public class Quick_Sort {
    
    public static void main(String[] args) {
        
        int[] arr = new int[10];

        System.out.println("1부터 100까지의 난수 10개를 생성합니다.\n");

        for(int i = 0; i < 10; i++) { // 10개의 난수 생성
            arr[i] = (int) (Math.random() * 100) + 1;
        }

        System.out.println("정렬 전 배열의 상태 출력");
        printArr(arr); 
        
        quickSort(arr); // 퀵 정렬

        System.out.println("정렬 후 배열의 상태 출력");
        printArr(arr);

    }

    // 퀵 정렬 시작
    private static void quickSort(int[] arr) {
        quickSort(arr, 0, arr.length - 1);
    }

    // 파티션을 나누면서 정렬 진행
    private static void quickSort(int[] arr, int st, int ed) {
        int part = partition(arr, st, ed);

        // 왼쪽  파티션
        if(st < part - 1) quickSort(arr, st, part - 1);

        // 오른쪽 파티션
        if(part < ed) quickSort(arr, part, ed);
    }

    // 파티션 구하기
    private static int partition (int[] arr, int st, int ed) {
        int pivot = arr[(st + ed) / 2]; // 피벗 설정 (중간 값)

        while(st <= ed) {
            while(arr[st] < pivot) st++; // 피벗보다 큰 값 탐색
            while(arr[ed] > pivot) ed--; // 피벗보다 작은 값 탐색

            // 교환
            if(st <= ed) {
                swap(arr, st, ed);
                st++; ed--;
            }
        }

        return st; // 새로운 파티션의 기준 인덱스 반환
    }

    private static void swap(int[] arr, int i, int j) {
        int tmp = arr[i];
        arr[i] = arr[j];
        arr[j] = tmp;
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
76 59 98 74 75 42 4 87 95 64

정렬 후 배열의 상태 출력
4 42 59 64 74 75 76 87 95 98
```

결과2

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
7 4 6 86 10 83 79 11 47 25 

정렬 후 배열의 상태 출력
4 6 7 10 11 25 47 79 83 86
```

---

### 퀵 정렬의 장점 & 단점

#### [장점]

1. **평균 시간 복잡도 O(N log N)**

- 대부분의 경우, 효율적으로 파티션이 분할되어 정렬 속도가 매우 빠름

- 병합 정렬보다 실제 실행 속도가 빠른 편 (비교 횟수와 이동 횟수가 적음)

&nbsp;

2. **추가 메모리 사용이 적음**
- 제자리 정렬
- 별도의 보조 배열이 거의 필요하지 않음

&nbsp;

3. **대규모 데이터에 적합**

- 평균적으로 다른 정렬 알고리즘보다 빠르고, 캐시 효율(Cache Locality)이 높음

 &nbsp;

#### [단점]

1. **최악의 경우 시간 복잡도 O(N²)**

- 이미 정렬된 배열에서 피벗을 부적절하게 선택하면
파티션이 한쪽으로 치우쳐 비효율적 분할 발생
→ ex) 항상 첫 번째나 마지막 원소를 피벗으로 선택한 경우

&nbsp;

2. **불안정 정렬 (Unstable Sort)**

- 값이 같은 원소들의 상대적인 순서가 보장되지 않음

- 안정성이 필요한 데이터(예: 이름/나이 같이 정렬)에는 부적합

&nbsp;

3. **재귀 호출에 따른 오버헤드 발생 가능**

- 재귀 깊이가 깊어질수록 스택 메모리 사용량이 증가

- 이를 방지하기 위해 비재귀(Iterative) 구현이나 피벗 개선 기법(Median-of-Three 등)을 사용하기도 함


---

### [퀵 정렬 참고 영상]

https://www.youtube.com/watch?v=8hEyhs3OV1w&t=41s