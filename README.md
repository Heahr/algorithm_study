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

스페이스바 없애기 ///Please do not touch anything -> Pleasedonottouchanything
```
#include <stdio.h>
#include <string.h>

int main() {

  //Please Enter Your Code Here
  char str[100000];
  scanf("%[^\n]s", str);
  
  for(int i = 0; i < 100000; i++) {
    if(str[i] == ' ') {
      continue;
    } else if(str[i] == '\0') {
      break;
    } else {
      printf("%c", str[i]);
    }
  }
  
  return 0;
}
```

문자열 정렬하기 
9		->
acid		-> acid
apple		-> acquire
banana		-> apple
acquire		-> banana
cat		-> cat
crop		-> cat
crab		-> crab
power		-> crop
cat		-> power
```
#include <stdio.h>
#include <string.h>

int main() {

  //Please Enter Your Code Here
  int num;
  scanf("%d", &num);
  
  char str[num][100];
  
  for(int i = 0; i < num; i++) {
    scanf("%s", str[i]);
  }
  
  char temp[1000];
  // char tmp;
  
  for(int i = 0; i < num; i++) {
    for(int j = i+1; j < num; j++) {
      int eq = strcmp(str[i], str[j]);
      if(eq == 0) {
        continue;
      } else if(eq > 0) {
        strcpy(temp, str[i]);
        strcpy(str[i], str[j]);
        strcpy(str[j], temp);
      }
    }
  }
  
  for(int i = 0; i < num; i++) {
    printf("%s", str[i]);
    printf("\n");
  }
  
  return 0;
}
```

문자열 포함 관계 Watermelon / melon -> YES
```
#include <stdio.h>
#include <string.h>

int main() {

  //Please Enter Your Code Here
  char str1[1000];
  char str2[1000];
  
  char temp[1000];
  
  scanf("%s", str1);
  scanf("%s", str2);
  
  int num1 = strlen(str1);
  int num2 = 0;
  int num3 = strlen(str2);
  
  int f = 0;
  
  for(int i = 0; i < num1; i++) {
    int inx = i;
    
    if(str1[i] == str2[num2]) {
      
      for(int j = 0; j < num3; j++) {
        if(str1[inx+j] != str2[j]) {
          break;
        } else if(j+1 == num3) {
          printf("YES");
          f = 1;
        }
        
      }
      
    }
    if(i+1 == num1) {
      printf("NO");
      break;
    } else if(f == 1) {
      break;
    }
  }
  
  return 0;
}
```

문자열 압축 AAABBBBBCCCCDDDDEFFF -> 3A5B4C4DE3F
```
#include <stdio.h>
#include <string.h>

int main() {

  //Please Enter Your Code Here
  char str[1000];
  scanf("%s", str);
  
  int num = strlen(str);
  
  int count = 0;
  int i, j;
  for(i = 0; i < num; i++) {
    if(str[i] == str[i+1]) {
      count++;
    } else if(str[i] != str[i+1] && count == 0) {
      printf("%c", str[i]);
    } else {
      printf("%d%c", count+1, str[i]);
      count = 0;
    }
  }
  
  return 0;
}
```

큰자리수 덧셈하기
123112981293812938139 -> 124411909784914159950
1298928491101221811
```
#include <stdio.h>
#include <string.h>

/*
void reverse(char *string, int num) {
  char temp;
  if(num % 2 == 0) {
    for(int i = 0; i < num; i++) {
      temp = string[i];
      string[i] = string[num-i];
      string[num-i] = temp;
    }
  } else {
    for(int i = 1; i <= num; i++) {
      temp = string[num+i];
      string[num+i] = string[num-i];
      string[num-i] = temp;
    }
  }
}

void sum(char *string1, char *string2, int num1, int num2) {
  int a;
  int q;
  int u = 0;
  int i;
  for(i = 0; i < num2; i++) {
    a = string1[i] + string2[i];
    q = (string1[i] + string2[i]) % 10;
    string1[i] = q + u;
    u = a / 10;
  }
  
  string1[i] += u;
  for(; i < num1; i++) {
    if(string1[i] > 10) {
      a = string1[i];
      string1[i] = string1[i] % 10;
      string1[i+1] += a / 10;
    }
  }
}
*/

#define StoD(X) ( X == 0 ? 0 : X - '0' )

void reverse(char *arr, int len) {
  char temp;
  int i;
  for(int i = 0; i < len/2; i++) {
    temp = arr[i];
    arr[i] = arr[len-1-i];
    arr[len-1-i] = temp;
  }
}

int main() {

  //Please Enter Your Code Here
  char a[3][100002];
  int len, i, j, up = 0;
  
  scanf("%s", a[0]);
  scanf("%s", a[1]);
  
  if(strlen(a[0]) > strlen(a[1])) {
    len = strlen(a[0]);
  } else len = strlen(a[1]);
  
  reverse(a[0], strlen(a[0]));
  reverse(a[1], strlen(a[1]));
  
  for(i = 0; i <= len; i++) {
    a[2][i] = (StoD(a[0][i]) + StoD(a[1][i]) + up) % 10 + '0';
    
    if((StoD(a[0][i]) + StoD(a[1][i]) + up) > 9) {
      up = 1;
    } else {
      up = 0;
    }
  }
  
  if(a[2][len] == '0') {
    a[2][len] = 0;
  }
  
  reverse(a[2], strlen(a[2]));
  
  printf("%s", a[2]);
  
  return 0;
}
```

mountain 
개인적으로 좀 재미있었다고 생각하는 이유중에 하나는 규칙이 일단 잘보였다는 이유가 하나가 될수 있을거같다. 이정도로 잘보였나? 이런규칙을 보고 하면 잘풀리구나 했던 기억이 있다.

3 -> 1213121
5 -> 1213121412131215121312141213121
```
#include <stdio.h>

int mountain (int num) {
  if(num > 0) {
    mountain(num-1);
    printf("%d", num);
    mountain(num-1);
  } else {
    return 0;
  }
}

int main() {

  //Please Enter Your Code Here
  int num;
  scanf("%d", &num);
  
  mountain(num);
  return 0;
}
```


순열구하기
4 2 ->
ab
ac
ad
ba
bc
bd
ca
cb
cd
da
db
dc
```
#include <stdio.h>
#include <string.h>

//int al[26] = {'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'};
int al[26] = {'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'};

int s(char *c, int num1, int num2, int num3) {
  if(num3 == 0) {
    for(int i = 0; i < num2; i++) {
      for( int j = 0; j < num2; j++) {
        if(i == j) {
          continue;
        } else if (c[i] == c[j]) {
          return 0;
        }
      }
    }
    for(int i = num2; i > 0; i--) {
      printf("%c", c[i-1]);
    }
    printf("\n");
  } else {
    for(int i = 0; i < num1; i++) {
      c[num3-1] = al[i]; 
      s(c, num1, num2, num3-1);
    }
  }
}

int main() {

  //Please Enter Your Code Here
  int num1, num2;
  scanf("%d %d", &num1, &num2);
  
  char t[num2];
  
  s(t, num1, num2, num2);
  return 0;
}
```


나누기
2	->897
< > 	  021

9			->9567843012
> < < < > > > < <	  1023765489
```
#include <stdio.h>
#include <string.h>

int f = 0;
int t = 0;

int inequal (char *str, int *arr, int num, int count) {
  if(f == 1) {
    return 0;
  }
  
  if(num+1 == count) {
    for(int i = 0; i < num+1; i++) {
      printf("%d", arr[i]);
    }
    f = 1;
    return 0;
  }
  
  for(int j = 9; j >= 0; j--) {
    //중복검사
    int c = 0;
    for(int k = 0; k < count; k++) {
      if(arr[k] == j) {
        c = 1;
        break;
      }
    }
    if(c == 1) {
      continue;
    }
    
    //첫값시작
    arr[count] = j;
    if(count == 0) {
      inequal(str, arr, num, count+1);
    }
    
    //맞으면 더들어가고 틀리면 나오기.
    if(str[count-1] == '<') {
      if(arr[count-1] < arr[count]) {
        inequal(str, arr, num, count+1);
      } else {
        continue;
      }
    } else if(str[count-1] == '>') {
      if(arr[count-1] > arr[count]) {
        inequal(str, arr, num, count+1);
      } else {
        continue;
      }
    }
  }
}

int outequal (char *str, int *arr, int num, int count) {
  if(t == 1) {
    return 0;
  }
  
  if(num+1 == count) {
    for(int i = 0; i < num+1; i++) {
      printf("%d", arr[i]);
    }
    t = 1;
    return 0;
  }
  
  for(int j = 0; j < 10; j++) {
    //중복검사
    int c = 0;
    for(int k = 0; k < count; k++) {
      if(arr[k] == j) {
        c = 1;
        break;
      }
    }
    if(c == 1) {
      continue;
    }
    
    //첫값시작
    arr[count] = j;
    if(count == 0) {
      outequal(str, arr, num, count+1);
    }
    
    //맞으면 더들어가고 틀리면 나오기.
    if(str[count-1] == '<') {
      if(arr[count-1] < arr[count]) {
        outequal(str, arr, num, count+1);
      } else {
        continue;
      }
    } else if(str[count-1] == '>') {
      if(arr[count-1] > arr[count]) {
        outequal(str, arr, num, count+1);
      } else {
        continue;
      }
    }
  }
}

int main() {

  //Please Enter Your Code Here
  int num;
  scanf("%d\n", &num);
  
  char str[num];
  for(int i = 0; i < num; i++) {
    scanf("%c ", &str[i]);
  }
  
  int arr[num];
  
  inequal(str, arr, num, 0);
  printf("\n");
  outequal(str, arr, num, 0);
  
  return 0;
}
```


합병정렬

10			-> -1 2 2 3 4 5 7 8 9 10
2 5 3 4 8 7 -1 9 10 2	  
```
#include <stdio.h>
int numbers[10000000];
void merging(int arr[], int s1, int e1, int s2, int e2) {
  int p, q;
  int temp[10000000];
  int temp_inx = 0;
  
  p = s1;
  q = s2;
  
  while (p <= e1 && q <= e2) {
    if(arr[p] <= arr[q]) {
      temp[temp_inx++] = arr[p];
      p++;
    } else {
      temp[temp_inx++] = arr[q];
      q++;
    }
  }
  
  if(p > e1) {
    for(int i = q; i <= e2; i++) {
      temp[temp_inx++] = arr[i];
    }
  } else {
    for(int i = p; i <= e1; i++) {
      temp[temp_inx++] = arr[i];
    }
  }
  
  for(int i = s1; i <= e2; i++) {
    arr[i] = temp[i-s1];
  }
}

void mergeSort(int arr[], int start, int end) {
  if(start >= end) {
    return;
  } else {
    int mid = (start+end) / 2;
    
    mergeSort(arr, start, mid);
    mergeSort(arr, mid+1, end);
    
    merging(arr, start, mid, mid+1, end);
  }
}

int main() {

  //Please Enter Your Code Here
  int n;
  
  
  scanf("%d", &n);
  
  for(int i = 0; i < n; i++) {
    scanf("%d", &numbers[i]);
  }
  
  mergeSort(numbers, 0, n-1);
  
  for(int i = 0; i < n; i++) {
    printf("%d ", numbers[i]);
  }
  return 0;
}
```


숫자박스
5
6 3 2 10 -10		-> 1 0 0 1 1 0 0 1
8
10 9 -5 2 3 4 5 -10
```
#include <stdio.h>

void merging(int arr[], int s1, int e1, int s2, int e2) {
  int p, q;
  int temp[10000000];
  int inx = 0;
  
  p = s1;
  q = s2;
  
  while(p <= e1 && q <= e2) {
    if(arr[p] <= arr[q]) {
      temp[inx++] = arr[p];
      p++;
    } else {
      temp[inx++] = arr[q];
      q++;
    }
  }
  
  if(p > e1) {
    for(int i = q; i <= e2; i++) {
      temp[inx++] = arr[i];
    }
  } else {
    for(int i = p; i <= e1; i++) {
      temp[inx++] = arr[i];
    }
  }
  
  for(int i = s1; i <= e2; i++) {
    arr[i] = temp[i-s1];
  }
}

void sort(int arr[], int start, int end) {
  if(start >= end) {
    return;
  } else {
    int mid = (start + end) / 2;
    
    sort(arr, start, mid);
    sort(arr, mid+1, end);
    
    merging(arr, start, mid, mid+1, end);
  }
}

int binarySearch(int arr[], int start, int end, int value) {
  if(start > end) {
    return -1;
  } else if(start == end) {
    if(arr[start] == value) {
      return start;
    } else {
      return -1;
    }
  } else {
    int mid = (start + end) / 2;
    if(arr[mid] == value) {
      return mid;
    } else if(arr[mid] > value) {
      return binarySearch(arr, start, mid-1, value);
    } else {
      return binarySearch(arr, mid+1, end, value);
    }
  }
}

int main() {

  //Please Enter Your Code Here
  int num;
  scanf("%d", &num);
  
  int arr[10000000];
  for(int i = 0; i < num; i++) {
    scanf("%d", &arr[i]);
  }
  
  sort(arr, 0, num-1);
  // for(int i = 0; i < num; i++) {
  //   printf("%d ", arr[i]);
  // }
  
  int num1;
  scanf("%d", &num1);
  
  int arr1[10000000];
  for(int i = 0; i < num1; i++) {
    scanf("%d", &arr1[i]);
  }

  for(int i = 0; i < num1; i++) {
    int a = binarySearch(arr, 0, num-1, arr1[i]);
    if(a == -1) {
      printf("0");
    } else {
      printf("1");
    }
    printf("\n");
  }

  return 0;
}
```
