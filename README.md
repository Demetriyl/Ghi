//Из целочисленного массива Х(N) все нечетные элементы записать в массив Y(k).
//Удалить из каждого массива все двузначные числа.
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
#include<malloc.h>
int main(void) {
  system("CHCP 1251");
  srand((unsigned)time(NULL));
  int size = (rand() % 25) + 1;
  int *X = (int*)malloc(40 * sizeof(int));
  int *Y = (int*)malloc(40 * sizeof(int));
  int flag = 0;
  int rewrite = 0;
  int rewritedv = 0;
  printf("Первый массив: \n");
  for (int i = 0; i<size; i++) {  
    int c = rand() % 500;
    X[i] = c;
    if ((c % 2) == 1) {
      Y[flag] = X[i];
      flag++;
    }
    printf("%i\n", X[i]);
  }
  printf("Второй массив: \n");
  for (int i = 0; i < flag; i++) {
    printf("%i\n", Y[i]);
  }
  printf("Первый массив без двузначных: \n");
  for (int i = 0; i < size; i++) {
    if (X[i] < 10  X[i] > 99) {
      X[rewrite] = X[i];
      rewrite++;
    }
  }
  for (int i = 0; i < rewrite; i++) {
    printf("%i\n", X[i]);
  }
  printf("Второй массив без двузначных: \n");
  for (int i = 0; i < flag; i++) {
    if (Y[i] < 10  Y[i] > 99) {
      Y[rewritedv] = Y[i];
      rewritedv++;
    }
  }
  for (int i = 0; i < rewritedv; i++) {
    printf("%i\n", Y[i]);
  }
  free(X);
  free(Y);
}
