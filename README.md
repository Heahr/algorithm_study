# algorithm_study

알고리즘 문제 풀었던것들 풀이.
상대적으로 쉬웠던 문제들은 제외하고 올림.

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

빙고판 (3빙고)
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int arr[5][5] = {0, };
  for(int i = 0; i < 5; i++) {
    for(int j = 0; j < 5; j++) {
      scanf("%d", &arr[i][j]);
    }
  }
  
  int num;
  int z;
  int f = 0;
  for(z = 1; z < 26; z++) {
    scanf("%d", &num);
    
    for(int i = 0; i < 5; i++) {
      for(int j = 0; j < 5; j++) {
        if(arr[i][j] == num) {
          arr[i][j] = 0;
        }
      }
    }
    
    for(int i = 0; i < 5; i++) {
      int b = 0;
      for(int j = 0; j < 5; j++) {
        if(arr[i][j] == 0) {
          b++;
        }
      }
      if(b == 5) {
        f++;
      }
    }
    
    for(int i = 0; i < 5; i++) {
      int b = 0;
      for(int j = 0; j < 5; j++) {
        if(arr[j][i] == 0) {
          b++;
        }
      }
      if(b == 5) {
        f++;
      }
    }
    
    if(!arr[0][0] && !arr[1][1] && !arr[2][2] && !arr[3][3] && !arr[4][4]) {
      f++;
    }
    
    if(!arr[0][4] && !arr[1][3] && !arr[2][2] && !arr[3][1] && !arr[4][0]) {
      f++;
    }
    
    if(f >= 3) {
      break;
    } else {
      f = 0;
    }
  }
  
  printf("%d", z);
  return 0;
}
```

공연장 대기열 만들기.
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int a, b;
  scanf("%d %d", &a, &b);
  int f;
  scanf("%d", &f);
  
  int arr[1100][1100] = {0, };
  int num1 = a;
  int num2 = b;
  
  int j=0;
  int o=b;
  
  int num = 1;
  
  a--;
  
  if(5 <= b && a <= 1000 && 1 <= a*b && a*b <= 100000000) {
    while(1) {
      for(int k = 0; k < b; k++) {
        o = o-1;
        arr[o][j] = num;
        num++;
      }
      b--;
      if(b < 0) {
        break;
      }
      
      for(int l = 0; l < a; l++) {
        j = j+1;
        arr[o][j] = num;
        num++;
      }
      a--;
      if(a < 0) {
        break;
      }
      
      for(int k = 0; k < b; k++) {
        o = o+1;
        arr[o][j] = num;
        num++;
      }
      b--;
      if(b < 0) {
        break;
      }
      
      for(int l = 0; l < a; l++) {
        j = j-1;
        arr[o][j] = num;
        num++;
      }
      a--;
      if(a < 0) {
        break;
      }
    }
  }
  
  
  
  int q = 0;
  int w = 0;
  for(int num3 = 0; num3 < num2; num3++) {
    for(int num4 = 0; num4 < num1; num4++) {
      if(f == arr[num3][num4]) {
        q = num3+1;
        w = num4+1;
      }
    }
  }
  
  q = num2 - q + 1;
  if(q == 0 || w == 0) {
    printf("0");
  } else {
    printf("%d %d", w, q);
  }
  
  
  // for(int num3 = 0; num3 < num2; num3++) {
  //   for(int num4 = 0; num4 < num1; num4++) {
  //   printf("%d ", arr[num3][num4]);
  //   }
  //   printf("\n");
  // }
  return 0;
}
```
