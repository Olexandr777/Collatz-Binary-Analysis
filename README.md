# Collatz-Binary-Analysis
202503@PL&gpt4based


"Коллатц в двоичной системе: битовый анализ"
взгляд на гипотезу Коллатца через объединение операций

Аннотация

Гипотеза Коллатца остаётся одной из самых известных проблем математики. В данной работе предлагается альтернативное представление последовательности Коллатца, основанное на объединении операций для нечётных чисел. Рассматривается переход от классической формулы (3x+1)/2 к эквивалентному представлению int(1.5x)+1 через битовую структуру числа.

Показано, что если у числа в двоичном представлении отбросить нули справа (деление на 2), получится нечетное число, начинающееся с единицы слева и заканчивающееся единицей справа, то количество операций int(1.5x)+1 (результат четное число) и последующее деление на 2 будет всегда одинаково. Это приводит к неизбежному уменьшению числа.
 
 
2. Объединение операций
 
2.1. Переписывание формулы Коллатца
 
В стандартном представлении для нечётных чисел операция 3x+1 всегда приводит к чётному числу, а значит, следом выполняется деление на 2:
(3x+1)/2


после анализа в двоичной системе можно переписать так:

(2x+x+1)/2 = x+x/2+0.5 = int(1.5x)+1

Здесь int(1.5x) обозначает целую часть числа 1.5x, что эквивалентно сложению числа x и его сдвинутой вправо версии - x/2, с потерей дробной части:
int(1.5x)=x+⌊x/2⌋, т.к. x - нечетное, то x/2 даст остаток 0.5, что в сумме с 1/2 дает +1 в формулу
 
 
2.2. Пример вычислений в двоичной системе
 
Рассмотрим десятичное число 11, двоичное x=01011b 


    01011.0 - x 
    00101.1 - x/2
    00000.1 - 1/2
    - - - - 
    10001.0 = 17


Результат совпадает с вычислением (3×11+1)/2=17, подтверждая эквивалентность формулы для нечетных чисел.

Прибавление 1 - это сумма двух половинок оставшихся при делении на 2. Это приводит к тому, что число всегда чётное, а значит, следом выполняется деление на 2.


для числа x=5 (0101​):

    0101.0
    0010.1
    0000.1
    ------
    1000.0   = 8

Результат совпадает с вычислением (3×5+1)/2=8, подтверждая эквивалентность формул.
 
 
3. Анализ динамики последовательности
 
3.1. Смещение бит
 
При рассмотрении последовательности в двоичной системе видно, что операция int(1.5x)+1 влияет на распределение бит:

    Перенос старшего бита влево возможен если установлены два старших бита или 3,4 слева.

    Второй бит справа также влияет на перенос вправо, если он установлен - результат будет четным (/2).

Для появления новых нулей справа будет больше комбинаций. Таким образом, количество уменьшений (делений на 2) превышает количество увеличений. 
Таким образом, число чаще сжимается, чем увеличивается. 
 
 
3.2. Баланс операций 1.5x+1 и /2
 
Если рассматривать число в двоичном представлении от первой слева единицы до первой справа единицы, можно заметить, что:

    Каждая операция 1.5x+1 создаёт чётное число.

    Чётное число делится на 2, следующие нули справа, если они есть, отбрасываются.

    Операции умножения и деления всегда чередуются.

Таким образом, баланс операций сохраняется, но учитывая операции с отброшенными нулями, количество комбинаций для сдвига влево меньше чем для сдвига вправо (реальное значение числа увеличивается в меньшее количество раз(1,5+1) чем уменьшается (/2)), можно предположить, что последовательность будет сжиматься.

