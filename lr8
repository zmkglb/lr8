import sys

flag = 1


def checkAnswer(summa):
    """
    Функция проверяет оканчивается ли число на цифру 4
    Входные данные:
    summa(int) - сумма чисел взятых из пар
    Функция ничего не возвращает. В случае того, что число оканчивается на 4 программа завершается
    """
    if summa % 10 == 4:
        print(summa)
        global flag
        if flag == 3:
            sys.exit()
        func("27-22b.txt")


def func(file):
    global flag
    flag = flag + 1
    size = 0
    sum = 0
    firstArray = []
    secondArray = []
    checkArray = []
    line = []

    """ читка данных из файла"""
    with open(file) as f:
        size = int(f.readline())
        for i in range(size):
            stroka = f.readline().split()
            firstArray.append(int(stroka[0]))
            secondArray.append(int(stroka[1]))

    """ Первый проход по парам и выборка минимального из каждой пары, запись их в сумму"""
    for i in range(size):
        if firstArray[i] < secondArray[i]:
            sum += firstArray[i]
            checkArray.append(1)
        else:
            sum += secondArray[i]
            checkArray.append(2)

    checkAnswer(sum)
    """ Сортировка пузырьком отнтсительно разности модулей чисел в кождой паре, что бы в дальнейшем
     прибавлять к сумме минимально возможные числа"""
    for i in range(size):
        j = size - 1
        while j > i:
            if (abs(firstArray[j - 1] - secondArray[j - 1])) > abs(firstArray[j] - secondArray[j]):
                fir = firstArray[j - 1]
                sec = secondArray[j - 1]
                check = checkArray[j - 1]
                firstArray[j - 1] = firstArray[j]
                secondArray[j - 1] = secondArray[j]
                checkArray[j - 1] = checkArray[j]
                firstArray[j] = fir
                secondArray[j] = sec
                checkArray[j] = check
            j = j - 1

    """ Первый проход по отсортированным массивам, выбираем минимальные """
    for i in range(size):
        if checkArray[i] == 1:
            sum -= firstArray[i]
            sum += secondArray[i]
            checkAnswer(sum)
            sum += firstArray[i]
            sum -= secondArray[i]
        else:
            sum -= secondArray[i]
            sum += firstArray[i]
            checkAnswer(sum)
            sum += secondArray[i]
            sum -= firstArray[i]


    """ все остальные проходы (перебор вохможных всех возможных комибинаций с движением от минимума к максимому)"""
    for i in range(size):
        j = i + 1
        while j < size:
            if checkArray[j] == 1:
                sum -= firstArray[j]
                sum += secondArray[j]
                checkAnswer(sum)
                sum += firstArray[j]
                sum -= secondArray[j]
            else:
                sum -= secondArray[j]
                sum += firstArray[j]
                checkAnswer(sum)
                sum += secondArray[j]
                sum -= firstArray[j]
            j = j + 1
        if checkArray[i] == 1:
            sum -= firstArray[i]
            sum += secondArray[i]
        else:
            sum -= secondArray[i]
            sum += firstArray[i]
    checkAnswer(sum)


func("27-22a.txt")
