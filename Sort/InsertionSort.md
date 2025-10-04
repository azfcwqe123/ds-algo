# Insertion Sort (삽입 정렬)

[그림]

![InsertionSort01](https://github.com/user-attachments/assets/64ac7744-d372-4937-8169-666276c29987)

![InsertionSort02](https://github.com/user-attachments/assets/d656fa40-f142-4650-b3e9-9e1078f2272a)

---

[코드]

```java
public class Insertion_Sort {
    public static void main(String[] args) {
        
        int[] arr = new int[10];

        System.out.println("1부터 100까지의 난수 10개를 생성합니다.\n");

        for(int i = 0; i < 10; i++) { // 10개의 난수 생성
            arr[i] = (int) (Math.random() * 100) + 1;
        }

        System.out.println("정렬 전 배열의 상태 출력");
        printArr(arr); 
        
        insertionSort(arr, arr.length); // 삽입 정렬

        System.out.println("정렬 후 배열의 상태 출력");
        printArr(arr);

    }

    private static void insertionSort(int[] arr, int len) {
        
        for(int i = 1; i < len; i++) {
            int target = arr[i]; // 현재 삽입할 요소

            int j = i - 1;

            // target보다 큰 요소들을 한 칸씩 뒤로 미룸
            while(j >= 0 && arr[j] > target) {
                arr[j + 1] = arr[j];
                j--;
            }

            // 반복문 종료시, 앞에 있는 요소가 더 작음(arr[j])
            // 그러므로 현재 요소는 j + 1 위치에 있어야함.
            arr[j + 1] = target; 
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
12 11 57 47 53 78 22 80 40 85

정렬 후 배열의 상태 출력
11 12 22 40 47 53 57 78 80 85
```

결과2

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
48 100 17 36 13 28 68 40 76 52

정렬 후 배열의 상태 출력
13 17 28 36 40 48 52 68 76 100
```

---

### 삽입 정렬의 장점 & 단점

#### [장점]

1. **최선의 경우 시간 복잡도 O(N)**

- 데이터가 이미 정렬되어 있을 경우, 비교만 하고 이동이 거의 없음

2. **구현이 단순하고 직관적**

- 현재 원소를 적절한 위치에 **삽입**하는 과정만 반복

3. **안정 정렬이 보장됨**

- 값이 같은 원소들의 상대적인 순서가 보장됨

- 예: 나이와 이름이 함께 주어진 데이터를 나이순으로 정렬할 때, 나이가 같은 사람들 사이에서 이름 순서가 유지됨

&nbsp;

#### [단점]

1. **평균 및 최악의 경우 시간 복잡도 O(N^2)**

- (n-1) + (n-2) + ... + 1 = n(n-1)/2 = O(N^2)

2. **교환(이동) 횟수가 많을 수 있음**

- 데이터가 역순으로 정렬되어 있는 경우, 거의 모든 원소를 계속 뒤로 밀어야 함

---

### [삽입 정렬 참고 영상]

https://www.youtube.com/watch?v=8oJS1BMKE64