# Selection Sort (선택 정렬)

[그림]

![SelectionSort01](https://github.com/user-attachments/assets/6a63b6ea-c827-49b8-88f3-b725eccf856d)

![SelectionSort02](https://github.com/user-attachments/assets/643c7284-ab3a-4ac3-b5a1-1a83cba858d6)

---

[코드]

```java
public class Selection_Sort {
    public static void main(String[] args) {
        
        int[] arr = new int[10];

        System.out.println("1부터 100까지의 난수 10개를 생성합니다.\n");

        for(int i = 0; i < 10; i++) { // 10개의 난수 생성
            arr[i] = (int) (Math.random() * 100) + 1;
        }

        System.out.println("정렬 전 배열의 상태 출력");
        printArr(arr); 
        
        selectionSort(arr, arr.length); // 선택 정렬

        System.out.println("정렬 후 배열의 상태 출력");
        printArr(arr);

    }

    // 선택 정렬
    private static void selectionSort(int[] arr, int len) {
        for(int i = 0; i < len - 1; i++) {
            int minIdx = i; // 교환 대상

            // 최솟값 탐색
            for(int j = i + 1; j < len; j++) {
                if(arr[j] < arr[minIdx]) {
                    minIdx = j;
                }
            }
            
            // 교환
            swap(arr, minIdx, i);
        }
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
22 68 60 28 61 92 61 49 44 56 

정렬 후 배열의 상태 출력
22 28 44 49 56 60 61 61 68 92
```

결과2

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
20 35 69 46 17 78 73 74 15 10

정렬 후 배열의 상태 출력
10 15 17 20 35 46 69 73 74 78
```

---

## 선택 정렬의 장점 & 단점

#### [장점]

1. 배열의 크기와 상관없이 항상 **N-1번** 교환이 발생
2. 구현이 매우 단순, 직관적

&nbsp;

#### [단점]

1. **시간 복잡도가 항상 O(N^2)**
- (n-1) + (n-2) + (n-3) + ... + 1 = n(n-1)/2 = O(N^2)


2. **불안정 정렬**
- 복합적인 데이터를 정렬할때, 값이 같은  원소끼리 있는 경우에 상대적인 위치가 변경될 수 있음.
- 예를 들어, 나이와 이름이 함께 주어진 데이터에서 나이순으로만 정렬할 경우, 나이가 같은 사람들 사이에서 이름 순서가 보장되지는 않음.

---

### [선택 정렬 참고 영상]

https://www.youtube.com/watch?v=92BfuxHn2XE