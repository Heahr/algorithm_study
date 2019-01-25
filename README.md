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

baseball 게임 만들기.

4개의 조건을 제시하고 그 조건에 부합하는 결과값이 얼마나 나오는지 출력하라.
-> 생각보다 조건에 맞는 정답을 찾는데 오랜시간이 걸렸다. 결과값에 자꾸 집착하다 보니 제시된 값들에 대해 접근하려 생각하지 않았다.
알고리즘을 계속해서 풀어가면서 이런 틀을 좀 계속해서 벗어나야 할 것 같다. 자꾸 생각이 갇히는 경우가 드문드문 발생한다.
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int run;
  while(1) {
    scanf("%d", &run);
    if(1 <= run && run <= 100){
      break;
    }
  }
  
  int count = 0;
  int f = 0;
  int s, b;
  
  int arr[101][5] = {0, };
  
  for(int i = 0; i < run; i++) {
    while(1) {
      scanf("%d", &arr[i][0]);
      if(1 <= arr[i][0] / 100 && arr[i][0] / 100 <= 9) {
        break;
      } else {
        continue;
      }
    }
    scanf("%d ", &arr[i][1]);
    scanf("%d\n", &arr[i][2]);
    // scanf("%d ", &arr[i][3]);
    // scanf("%d", &arr[i][4]);
  }
  for(int i = 1; i < 10; i++) {
    for(int j = 1; j < 10; j++) {
      for(int k = 1; k < 10; k++) {
        if(i == j || j == k || k == i) {
          continue;
        }
        for(int z = 0; z < run; z++) {
          
          if(i == arr[z][0] / 100){
            s++;
          } else if (i == arr[z][0] / 10 - (arr[z][0] / 100) * 10) {
            b++;
          } else if (i == arr[z][0] - (arr[z][0] / 10) * 10) {
            b++;
          }
          
          if(j == arr[z][0] / 10 - (arr[z][0] / 100) * 10){
            s++;
          } else if (j == arr[z][0] / 100) {
            b++;
          } else if (j == arr[z][0] - (arr[z][0] / 10) * 10) {
            b++;
          }
          
          if(k == arr[z][0] - (arr[z][0] / 10) * 10){
            s++;
          } else if (k == arr[z][0] / 10 - (arr[z][0] / 100) * 10) {
            b++;
          } else if (k == arr[z][0] / 100) {
            b++;
          }
          if(s == arr[z][1] && b == arr[z][2]) {
            count++;
            s = 0;
            b = 0;
          } else {
            s = 0;
            b = 0;
          }
        }
        
        if(count == run) {
          f++;
          count = 0;
        } else {
          count = 0;
        }
      }
    }
  }
  
  printf("%d", f);
  return 0;
  
}
```

직사각형 네 개의 합집합 면적 구하기
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int arr[100][100] = {0,};
  
  int a,b,c,d;
  for(int z = 0; z < 4; z++) {
    scanf("%d %d %d %d", &a ,&b ,&c ,&d);
    for(int i = a ; i < c; i++) {
      for(int j = b ; j < d; j++) {
        arr[i][j] = 1;
      }
    }
  }
  
  int count = 0;
  for(int i = 0; i < 100; i++) {
    for(int j = 0; j < 100; j++) {
      if(arr[i][j] == 1) {
        count++;
      }
    }
  }
  
  printf("%d", count);
  return 0;
}
```

원하는 횟수의 큰 수 찾기
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int n, arr[100010];
  int a;
  
  scanf("%d ", &n);
  scanf("%d\n", &a);
  
  for(int i = 0; i < n; i++) {
    scanf("%d", &arr[i]);
  }
  
  for(int i = 0; i < n; i++) {
    for(int j = 0; j < n-i-1; j++) {
      if(arr[j] > arr[j+1]) {
        int temp;
        temp = arr[j];
        arr[j] = arr[j+1];
        arr[j+1] = temp;
      }
    }
    
    if(i+1 == a) {
      printf("%d", arr[n-a]);
      break;
    }
  }
  
  return 0;
}
```

```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int count;
  scanf("%d", &count);
  
  int arr[count];
  for(int i = 0; i < count; i++) {
    scanf("%d", &arr[i]);
  }
  
  int num = 0;
  for(int i = 0; i < count; i++) {
    if(i == 0) {
      printf("%d ", arr[i]);
      num = num + arr[i];
      continue;
    }
    
    for(int j = 0; j < 10000000; j++) {
      if((num + j)/(i+1) == arr[i]) {
        printf("%d ", j);
        num = num + j;
        break;
      }
    }
  }
  return 0;
}
```

벌꿀집 모양 값 찾기. ex) 입력값 13 -> 출력값 3, 입력값 58 -> 출력값 5
```
#include <stdio.h>

int main() {

  //Please Enter Your Code Here
  int num;
  scanf("%d", &num);
  
  int limit = 1000000;
  int num1 = 1;
  for(int i = 0; i < limit; i++) {
    if(num == 1) {
      printf("1");
      break;
    } else if (num1 <= num && num <= num1 + (i+1)*6) {
      printf("%d", i+2);
      break;
    } else {
      num1 = num1 + (i+1)*6;
    }
  }
  return 0;
}
```

입력값중 소수찾기 ex) 입력 -> 4 1 3 5 7 출력-> 3
```
#include <stdio.h>

int prime( int a );

int main() {
	int input;
	scanf( "%d", &input );
	
	int arr[input];
	for(int i = 0; i < input; i++) {
	  scanf("%d ", &arr[i]);
	}

  int count = 0;
	for(int i = 0; i < input; i++) {

		if( prime(arr[i]) == 1 ) {
		  count++;
		}
		//if( prime(input) == 0 )	-> 소수가 아님.
	}
  
  printf("%d", count);
	return 0;
}

int prime( int a )
{
	int j;

	for( j=2 ; j<=a ; j++ )
	{
		if( a%j == 0 )
		{
			if( a == j )	return 1;
			if( a != j )	return 0;
		}
	}

	return 0;
}
```


```

```
