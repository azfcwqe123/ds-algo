# Shell Sort (쉘 정렬)

[그림]

![ShellSort01](https://github.com/user-attachments/assets/819f097c-3cb1-40ce-a6f8-f642def3104e)

![ShellSort02](https://github.com/user-attachments/assets/ead72da2-be67-4236-b268-9668b5626a44)

![ShellSort03](https://github.com/user-attachments/assets/c97c21e9-68ba-4180-80dd-30a27ab56724)

---

[코드]

```java
public class Shell_Sort {
    
    public static void main(String[] args) {
        
        int[] arr = new int[10];

        System.out.println("1부터 100까지의 난수 10개를 생성합니다.\n");

        for(int i = 0; i < 10; i++) { // 10개의 난수 생성
            arr[i] = (int) (Math.random() * 100) + 1;
        }

        System.out.println("정렬 전 배열의 상태 출력");
        printArr(arr); 
        
        shellSort(arr, arr.length); // 쉘 정렬

        System.out.println("정렬 후 배열의 상태 출력");
        printArr(arr);

    }

    // 쉘 정렬
    private static void shellSort(int[] arr, int len) {
        for(int gap = len / 2; gap > 0; gap /= 2) {
            if(gap % 2 == 0) gap++; // 홀수 gap이 짝수 gap보다 효율적 → 배열 전체가 고르게 섞임
            for(int i=0; i<gap; i++) {
                insertionSort(arr, i, len - 1, gap);
            }
        }

    }

    // 삽입 정렬
    private static void insertionSort(int[] arr, int st, int ed, int gap) {
        
        for(int i = st + gap; i <= ed; i += gap) {
            int target = arr[i]; 

            int j = i - gap;

            while(j >= st && arr[j] > target) {
                arr[j + gap] = arr[j];
                j -= gap;
            }

            arr[j + gap] = target; 
        }
    }

    private static void printArr(int[] arr) {
        for (int x : arr) {
            System.out.print(x + " ");
        }
        System.out.println("\n");
    }
}
=
```

결과1

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
25 51 10 49 21 26 79 8 65 29

정렬 후 배열의 상태 출력
8 10 21 25 26 29 49 51 65 79
```

결과2

```
1부터 100까지의 난수 10개를 생성합니다.

정렬 전 배열의 상태 출력
43 1 15 33 61 55 58 99 22 40

정렬 후 배열의 상태 출력
1 15 22 33 40 43 55 58 61 99 
```

---

## 버블 정렬의 장점 & 단점

#### [장점]

1. **삽입 정렬보다 효율적**
- 큰 gap으로 먼 거리 요소를 먼저 이동 → 작은 값이 맨 앞으로 빠르게 이동

2. **홀수 gap 활용 시 효율적**
- 요소들이 그룹을 겹쳐 이동 → 한 단계에서도 많은 요소가 올바른 위치로 가까워짐

&nbsp; 

#### [단점]

1. **시간 복잡도는 최악의 경우 O(N^2), 평균적으로는 O(N^1.5)**
&nbsp;

2. **짝수 gap 사용 시 효율 제한**
- 같은 그룹끼리만 이동 → 일부 요소는 한 단계에서 정렬되지 않음

3. **일반적으로 안정적이지 않음**
- 같은 값의 원소가 서로 다른 그룹에 속하면 순서가 바뀔 수 있음

ex) 안정성을 보장하지 못하는 경우
```
gap = 2일때,

A[5], B[5], C[3], D[5]이면

C[3] - B[5] - A[5] - D[5]와 같이 정렬됨.

A가 B보다 앞에 있어야하는데 그러질 못함. 안정성 보장X
```

&nbsp;

쉘 정렬은 마지막에 gap = 1이 실행되면서, 배열을 완전히 정렬시킴.

---

### [쉘 정렬 참고 영상]

https://www.youtube.com/watch?v=n4sk-SzGvZA