# 선택 정렬 (Selection Sort)

가장 작은 값을 탐색한다음 swap을 통해 앞부분에 배치시키는 정렬방식이다.

1. 0번 인덱스 ~ n번 인덱스 중 가장 작은 값을 찾아 0번째 인덱스와 swap한다
2. 1번 인덱스 ~ n번 인덱스 중 가장 작은 값을 찾아 1번째 인덱스와 swap한다…
3. n-1번 인덱스 ~ n번 인덱스 중 가장 작은 값을 찾아 n번째 인덱스와 swap한다

버블 정렬이 각 회전이 끝날 때마다 맨 마지막 데이터의 위치가 정해졌던 것과 반대로

**선택 정렬은 n번째 회전이 끝날 때마다 앞에서 n번째 데이터의 위치가 정해진다.**

### **Big O**

- **Worst Case: O(n^2)**: 정렬이 하나도 안되어있는 경우
- **Best Case: O(n^2)**: 이미 정렬이 되어있는 경우

선택 정렬은 정렬이 이미 되어있는 경우에도 O(n^2)의 시간 복잡도를 가진다.

그 이유는 매번 정해진 자리에 올 수 있는 최소값을 찾아야하기 때문이다. 그렇기 때문에 성능이 매우 떨어진다.

### **장점**

선택 정렬도 **in place** 알고리즘이기 때문에 **메모리가 절약된다**는 장점이 있으며 알고리즘이 직관적이므로 이해하기도 쉽고 구현하기도 쉽다.

### **단점**

선택 정렬은 **최선의 경우에도, 최악의 경우에도** **O(n^2)**의 시간이 걸리는 만큼 **성능이 매우 떨어진다.**

### **UnStable**

선택 정렬은 데이터가 중복된 경우 위치가 바뀔 수 있기 때문에 **Unstable한 정렬**이다.

## javaScript에서의 구현

```js
function selectionSort(array) {
  for (let i = 0; i < array.length; i++) {
    //첫 번째 요소 min에 저장
    let min = i;
    //반복문으로 min과 다음요소 비교하여 최솟값을 min에 할당
    for (let j = i + 1; j < array.length; j++) {
      if (array[min] > array[j]) {
        min = j;
      }
    }
    //만약 min이 최초의 저장한 값이 아니라면 Swap
    if (min !== i) {
      let swap = array[min];
      array[min] = array[i];
      array[i] = swap;
    }
    console.log(`${i}회전: ${array}`);
  }
  return array;
}
console.log(selectionSort([5, 4, 3, 2, 1]));
```
