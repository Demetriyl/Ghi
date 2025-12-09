#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Функция очистки памяти в случае ошибки
void freeArray(int** arr, int rows) {
    for (int i = 0; i < rows; i++) {
        if (arr[i] != NULL) {
            free(arr[i]);
        }
    }
    free(arr);
}

// Функция создания и заполнения массива
int** createAndFillArray(int rows, int cols) {
    // 1. Исправление: arr должен быть int**, приведение типов при malloc
    int** arr = (int**)malloc(rows * sizeof(int*));
    if (arr == NULL) {
        perror("Ошибка выделения памяти для указателей строк");
        return NULL;
    }

    for (int i = 0; i < rows; i++) {
        // 2. Исправление: приведение типов при malloc
        arr[i] = (int*)malloc(cols * sizeof(int));
        if (arr[i] == NULL) {
            perror("Ошибка выделения памяти для строки");
            // 3. Исправление: Очистка уже выделенной памяти перед выходом
            freeArray(arr, i);
            return NULL;
        }

        for (int j = 0; j < cols; j++) {
            arr[i][j] = rand() % 100; // числа от 0 до 99
        }
    }
    return arr;
}

int main() {
    int rows = 50, cols = 50;

    srand(time(NULL)); // инициализация генератора случайных чисел

    int** matrix = createAndFillArray(rows, cols);

    if (matrix == NULL) {
        return 1; // Выход из программы, если выделение памяти не удалось
    }

    // Вывод массива
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            printf("%3d ", matrix[i][j]);
        }
        printf("\n");
    }

    // Освобождение памяти
    // Используем новую функцию очистки для единообразия
    freeArray(matrix, rows);

    return 0;
}
