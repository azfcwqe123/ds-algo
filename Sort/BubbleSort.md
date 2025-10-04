# Bubble Sort (선택 정렬)

[그림]

![BubbleSort01](https://github.com/user-attachments/assets/5ce4720f-79b6-4133-be61-5f0e45b13534)

![BubbleSort02](https://github.com/user-attachments/assets/fe9d6e8a-b3dc-420e-b330-ef40d997b0b1)

![BubbleSort03](https://github.com/user-attachments/assets/b66f656a-4849-4062-a4c9-95acddd27261)

---

[코드]

```java
public class Bubble_Sort {
    public static void main(String[] args) {
        
        int[] arr = new int[10];

        System.out.println("1부터 100까지의 난수 10개를 생성합니다.\n");

        for(int i = 0; i < 10; i++) { // 10개의 난수 생성
            arr[i] = (int) (Math.random() * 100) + 1;
        }

        System.out.println("정렬 전 배열의 상태 출력");
        printArr(arr); 
        
        bubbleSort(arr, arr.length); // 선택 정렬

        System.out.println("정렬 후 배열의 상태 출력");
        printArr(arr);

    }

    // 버블 정렬
    private static void bubbleSort(int[] arr, int len) {
        for(int i = 0; i < len - 1; i++) {
            for(int j = 0; j < len - i - 1; j++) {
                if(arr[j] > arr[j+1]) {
                    swap(arr, j, j + 1);
                }
            }
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
60 93 57 38 86 42 61 60 73 97

정렬 후 배열의 상태 출력
38 42 57 60 60 61 73 86 93 97
```

결과2

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
77 78 18 99 87 32 28 67 23 54

정렬 후 배열의 상태 출력
18 23 28 32 54 67 77 78 87 99
```

---

## 버블 정렬의 장점 & 단점

#### [장점]

1. **구현이 매우 단순, 직관적**

2. **안정 정렬**

- 값이 같은 원소들의 상대적인 순서가 유지됨

- ex) 나이순으로 정렬할 때, 같은 나이의 사람들은 입력 순서가 보존됨

&nbsp; 

#### [단점]

1. **시간 복잡도가 항상 O(N^2)**

- (n-1) + (n-2) + (n-3) + ... + 1 = n(n-1)/2 = O(N^2)

2. **최선, 평균, 최악 모두 O(N^2)**

- 교환 횟수가 많음

- 작은 값이 맨 앞으로 이동하기 위해 매번 한 칸씩 교환되어야 함

- 다른 단순 정렬(선택, 삽입)에 비해 비효율적

---

### [버블 정렬 참고 영상]

https://www.youtube.com/watch?v=Cq7SMsQBEUw