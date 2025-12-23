#include <iostream>
#include <windows.h>
#include <cstdlib>
#include <cstdio>
#include <ctime>
#include <locale.h>

int main(int argc, char* argv[], char* env[]) {
    SetConsoleOutputCP(1251);
    SetConsoleCP(1251);
    system("CHCP 1251");
    setlocale(LC_ALL, "rus");
    srand(time(0));

    printf_s("Количество аргументов командной строки: %i \n", argc);
    printf("Аргументы командной строки:\n");
    for (int i = 0; i < argc; i++) {
        printf_s("%s\n", argv[i]);
    }

    if (argc != 4) {
        printf("Не хватает элементов");
        return 0;
    }

    double num1 = atoi(argv[1]);
    int num2 = atoi(argv[3]);
    char num3 = argv[2][0];
    double num;

    printf(" %i %i %c\n", num1, num2, num3);

    if (num3 == '+') {
        num = num1 + num2;
        printf_s("%f\n", num);
    }
    if (num3 == '-') {
        num = num1 - num2;
        printf_s("%f\n", num);
    }
    if (num3 == 'x') {
        num = num1 * num2;
        printf_s("%f\n", num);
    }
    if (num3 == '/' && num2 != 0) {
        num = num1 / num2;
        printf_s("%f\n", num);
    }
    if (num3 == '/' && num2 == 0) {
        printf("Невозможно поделить на нуль");
    }

    return 0;
}
