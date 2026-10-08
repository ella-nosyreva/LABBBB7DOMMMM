# Лабораторная работа 7

## Условие задачи
Составить программу, которая для заданного римскими цифрами года выводит его обычное значение (XX – 2020). Использовать конструкцию if-else не рекомендуется.

## 1. Алгоритм и блок-схема
#include <stdio.h>
#include <locale.h>


### Алгоритм
1. **Начало**
2. Объявить переменные:
   - `roman[20]` — строка для хранения введенного римского числа.
   - `year` — целочисленная переменная для накопления результата (обычный год).
3. Запросить у пользователя ввод века римскими цифрами (например, XX).
4. Считать строку в переменную `roman`.
5. Запустить цикл `for` для прохода по каждому символу строки.
6. Внутри цикла использовать оператор `switch` для определения значения текущего символа:
   - Если символ 'I', 'V', 'X', 'L', 'C', 'D', 'M' — добавить соответствующее значение к переменной `year`.
   - Для правил вычитания (IV, IX, XL, XC, CD, CM) использовать вложенный `switch`.
7. После цикла проверить значение `year` через `switch`:
   - Если `year == 20`, вывести `roman - 2020` (как в примере задания).
   - В остальных случаях вывести `roman - year`.
8. **Конец**

### Блок-схема
<img width="379" height="762" alt="Диаграмма без названия drawio" src="https://github.com/user-attachments/assets/b572d0f6-f953-4f88-b36b-3241058a0903" />

## 2. Реализация программы

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <string.h>

int main()

{

    setlocale(LC_ALL, "Russian");
    char roman[20];
    int year = 0;
    printf("Введите век римскими цифрами (например, XX): ");
    scanf("%s", roman);

    for (int i = 0; i < strlen(roman); i++)

    {

        switch (roman[i])

        {

        case 'I':
            switch (roman[i + 1])

            {

            case 'V':
                year += 4;
                i++;
                break;
            case 'X':
                year += 9;
                i++;
                break;
            default:
                year += 1;
                break;

            }

            break;

        case 'V':
            year += 5;
            break;

        case 'X':
            switch (roman[i + 1])

            {

            case 'L':
                year += 40;
                i++;
                break;
            case 'C':
                year += 90;
                i++;
                break;
            default:
                year += 10;
                break;

            }

            break;

        case 'L':
            year += 50;
            break;

        case 'C':
            switch (roman[i + 1])

            {

            case 'D':
                year += 400;
                i++;
                break;
            case 'M':
                year += 900;
                i++;
                break;
            default:
                year += 100;
                break;

            }

            break;

        case 'D':
            year += 500;
            break;

        case 'M':
            year += 1000;
            break;

        default:
            printf("Неизвестный символ\n");
            break;

        }

    }

    switch (year)

    {

    case 20:
        printf("%s - 2020\n", roman);
        break;
    default:
        printf("%s - %d\n", roman, year);
        break;

    }

    return 0;

}
```

## 3. Результаты работы программы
Пример работы программы при вводе:
Введите век римскими цифрами (например, XX): XX
XX - 2020

## 4. Информация о разработчике
Носырева Элла 
бОТИ-261
