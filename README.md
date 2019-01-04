# algorithm_study

알고리즘 문제 풀었던것들 풀이.
쉬운것들은 패스하고 정리함.

삼각형 출력
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int a, i, j;
  scanf("%d", &a);
  
  for(i = 1; i <= a; i++) {
    for(j = a; j >= 1; j--) {
      if(i < j) {
        printf(" ");
      } else {
        printf("*");
      }
    }
    for(int k = 1; k < i; k++) {
      printf("*");
    }
    printf("\n");
  }
  
  
  return 0;
}
```

소수판별
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int a;
  scanf("%d", &a);
  
  for(int i = 2; i <= a; i++) {
    if(i == a) {
      printf("YES");
      break;
    } else if(a%i == 0) {
      printf("NO");
      break;
    } else {
      continue;
    }
  }
  return 0;
}
```

윤년
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int a = 0;
  scanf("%d", &a);
  
  if(a % 100 != 0 && a % 4 == 0) {
    printf("YES");
  } else {
    if(a % 400 == 0) {
      printf("YES");
    } else {
      printf("NO");
    }
  }
  return 0;
}
```

숫자 피라미드
ex)입력 -> 5 3
     3
    456
   21987
  3456789
 987654321
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  //
  int a, b;
  scanf("%d %d", &a, &b);
  
  int c = a;
  
  int arr[a][a*2] = {0, };
  for(int i = 1; i <= a; i++) {
    for(int j = 0; j < i*2-1; j++) {
      arr[i-1][j] = b;
      b++;
      if(b == 10) {
        b = 1;
      }
    }
  }
  
  for(int i = 1; i <= a; i++) {
    
    for(int j = c; j > i; j--) {
      printf(" ");
    }
    
    if(i % 2 == 0) {
      for(int j = 0; j < i*2-1; j++) {
        printf("%d", arr[i-1][j]);
      }
    } else {
      for(int j = i*2-2; j >= 0; j--) {
        printf("%d", arr[i-1][j]);
      }
    }
    printf("\n");
  }
  return 0;
}
```

대표값
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int arr[100] = {0, };
  
  int num = 0;
  for(int i = 0; i < 10; i++) {
    scanf("%d", &arr[i]);
    num += arr[i];
  }
  num = num / 10;
  int a = 0;
  int b = 0;
  int c = 0;
  for(int i = 0; i < 10; i++) {
    for(int j = 0; j < 10; j++) {
      if(arr[i] == arr[j]) {
        b++;
      }
    }
    if(a < b) {
      a = b;
      c = i;
    }
    b = 0;
  }
  
  printf("%d\n%d", num, arr[c]);
  return 0;
}
```


```
```
