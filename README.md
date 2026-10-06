# Homework-4
# Решение задачи «Выбор маршрута»

## 1. Условие задачи
На развилке дорог стоит знак. Он показывает направление "Налево", если только одно из двух чисел (A или B), полученных от датчиков traffic flow, является четным. Запишите условие для показа направления "Налево".

Логическое условие:

Условие истинно (равно 1), когда: condition = (A (mod 2) == 0 И B (mod 2) != 0) ИЛИ (A (mod 2) != 0 И B (mod 2) == 0                
Или в сокращённой форме с использованием битового/логического исключающего ИЛИ (XOR):condition = (A (mod 2) == 0) != (B (mod 2) == 0).

# 2. Структура блок-схемы.

https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=%D0%94%D0%B8%D0%B0%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0%20%D0%B1%D0%B5%D0%B7%20%D0%BD%D0%B0%D0%B7%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20name%3D%22%D0%A1%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0-1%22%20id%3D%22H9XSfu5xaMsdC_y1zsnS%22%3E5VjbctowEP2WPngmPKTjCzbwyCVJ%2B9BOO%2Bm0zVNHwcKoEZZHFmD69V1Z8g2TgKmBtGUyzup4V5fdo4OQ4YwXyR1H0fwD8zE1bNNPDGdi2LZlOib8k8hGIa5nKyDgxNdOBXBPfuEsUqNL4uO44igYo4JEVXDKwhBPRQVDnLN11W3GaHXUCAW4BtxPEa2j34gv5grt270Cf4dJMM9GtryBevOIpk8BZ8tQj0el07WP%2BNOVYTu36cewx7ndUWELlI2hExDPkc%2FWJci5MZwxZ0woa5GMMZU5z9Kp4m6feZuvh%2BNQHBKQBF9WH%2BnPh88Pzg%2FvazROImd9vaMXDcVik6UO%2BoEqQWO0nhOB7yM0lW%2FWQBTA5mJBoWWBCUuM8PswhkpniODsCY8ZZRyQaurM9KNSp%2BwORMwIpbv9d6XaGQUc%2BQQmn8WELJQznbECOmRYtegVoku9aMP2KGRk9AhGIA1jYhqjSfo0DVhcv5fZ8FRvb7IgqEIRp3rGXOCklGFdpDvMFljwDbjMS%2FTra9KsC6paGZF0L46r29mG1E2kN0qQ91yQAgzNiwYc0fsc%2B7UNVicNW%2FIp3s%2B3MrlCfyi3N7SmFMUxmVY5le48LOdnQgsnRHyX9ltXtx60n7QnScltstGN5hyMBeJCS1g%2FLyGAARYvLM7ZQaJ9hc6qxjFFgqyqGS5V%2F6Xq6hE%2BMQLlKPgxqPLDsbe6UMXSUWXh2Oqoa1U7sgZbHanE1DpKyZYv%2B3j%2BOYdoVCo9YIIXohRTBrqwgNJFmBOYAObb7z4VL5rL2owkOPuOs44QrSNksXU9G6Yh5qg1zfKaa5bVO5VodVsULecCotW03s0ZdaCouf%2BHqOXfuGcSNfcQUavSaI9KNWXM6TVrvwbBYd8nnLAQ%2FFIX8%2BpqKG0b8mPaGk1fmCnsoYVctnrWmlLMSrFvZOI6HYn1xvIv8w8fYx2%2FQ%2FkU5pPVNpT7bE0xHab57IqVySk%2BPxPAKpM5QpkHdWXOMd2L7bnV%2FXCy46TXojK7f6jMTffMeY6fr1txrZYU1znzMbL3PM1eyzHy9L%2BW2z9GphIuUgm%2F3DmyxqXW1GrQolr1LnCO%2FMfUx%2B22pD7dM6tPNvzJbtr%2Bxp%2Bg6aXZUF%2BdFddrbnq95l3yMq1GjwMEBZrFba7iTXGV7tz8Bg%3D%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E

https://github.com/user-attachments/assets/7885d973-2d34-4355-b5fb-7eebc53a83f0

# 3. Исходный код решения.

```c
#include <stdio.h>
#include <locale.h>

#ifdef _WIN32
#include <windows.h>
#endif

int main(void) {

#ifdef _WIN32
    SetConsoleOutputCP(65001);
    SetConsoleCP(65001);
#endif
    setlocale(LC_ALL, "Russian");

    int A, B;
    int condition;

    printf("Система управления знаком на развилке\n");
    printf("Введите два целых числа от датчиков traffic flow (A и B): ");

    if (scanf_s("%d %d", &A, &B) != 2) {
        printf("Ошибка ввода данных!\n");
        return 1;
    }

    condition = ((A % 2 == 0 && B % 2 != 0) || (A % 2 != 0 && B % 2 == 0));

    printf("\nРезультат:\n");
    printf("Показывать направление \"Налево\" (1 - да, 0 - нет): %d\n", condition);

    if (condition) {
        printf("Знак указывает: НАЛЕВО\n");
    }
    else {
        printf("Знак НЕ указывает налево\n");
    }

    return 0;
}
```
# 4. Пример работы программы.

Система управления знаком на развилке                                               
Введите два целых числа от датчиков traffic flow (A и B): 4 7

Результат:                                        
Показывать направление "Налево" (1 - да, 0 - нет): 0                   
Знак НЕ указывает налево

# 5. Информация о разработчике.

Работу делал студент группы бИЦТ-261 Есин А. А.
