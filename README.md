# Домашнее задание к занятию "7.5. Основы golang"

С `golang` в рамках курса, мы будем работать не много, поэтому можно использовать любой IDE. 
Но рекомендуем ознакомиться с [GoLand](https://www.jetbrains.com/ru-ru/go/).  

## Задача 1. Установите golang.
1. Воспользуйтесь инструкций с официального сайта: [https://golang.org/](https://golang.org/).
2. Так же для тестирования кода можно использовать песочницу: [https://play.golang.org/](https://play.golang.org/).

Решение:

- установим GoLang
```
scp  ./go1.19.1.linux-amd64.tar.gz vagrant@192.168.33.10:/home/vagrant/
vagrant@vagrant:~/go-lang$ sudo tar -C /usr/local -xzf go1.19.1.linux-amd64.tar.gz
vagrant@vagrant:~/go-lang$ go version
go version go1.19.1 linux/amd64
```

## Задача 2. Знакомство с gotour.
У Golang есть обучающая интерактивная консоль [https://tour.golang.org/](https://tour.golang.org/). 
Рекомендуется изучить максимальное количество примеров. В консоли уже написан необходимый код, 
осталось только с ним ознакомиться и поэкспериментировать как написано в инструкции в левой части экрана.  

## Задача 3. Написание кода. 
Цель этого задания закрепить знания о базовом синтаксисе языка. Можно использовать редактор кода 
на своем компьютере, либо использовать песочницу: [https://play.golang.org/](https://play.golang.org/).

1. Напишите программу для перевода метров в футы (1 фут = 0.3048 метр). Можно запросить исходные данные 
у пользователя, а можно статически задать в коде.
    Для взаимодействия с пользователем можно использовать функцию `Scanf`:
    ```
    package main
    
    import "fmt"
    
    func main() {
        fmt.Print("Enter a number: ")
        var input float64
        fmt.Scanf("%f", &input)
    
        output := input * 2
    
        fmt.Println(output)    
    }
    ```
Решение:
```
vagrant@vagrant:~/go-lang$ cat Meters-Funt.go
package main

import (
        "fmt"
        "os"
)

const foot = 0.3048

func m2f(meter float32) float32 {
        return meter / foot
}

func main() {
        var value float32
        fmt.Print("Введите кол-во метров для перевода: ")
        fmt.Fscan(os.Stdin, &value)
        fmt.Printf("Кол-во футов - %9.2f\n", m2f(value))
}
vagrant@vagrant:~/go-lang$ go run Meters-Funt.go
Введите кол-во метров для перевода: 45
Кол-во футов -    147.64
```
 
1. Напишите программу, которая найдет наименьший элемент в любом заданном списке, например:
    ```
    x := []int{48,96,86,68,57,82,63,70,37,34,83,27,19,97,9,17,}
    ```

Решение:

```
vagrant@vagrant:~/go-lang$ cat array.go
package main

import (
        "fmt"
)

func lowest_number(array []int) int {
        var min_value int = 0

        for index_value := 0; index_value < len(array); index_value++ {
                if index_value == 0 {
                        min_value = array[index_value]
                } else {
                        if array[index_value] < min_value {
                                min_value = array[index_value]
                        }
                }
        }
        return min_value
}

func main() {
        var x = []int{48, 96, 1, 86, 68, 57, 82, 63, 70, 37, 34, 83, 27, 19, 97, 9, 17, 6, 98}
        fmt.Println(lowest_number(x))
}
vagrant@vagrant:~/go-lang$ go run array.go
1
```


1. Напишите программу, которая выводит числа от 1 до 100, которые делятся на 3. То есть `(3, 6, 9, …)`.

Решение:
```
vagrant@vagrant:~/go-lang$ cat Div3.go
package main

func init_array(p [100]int) [100]int {
        for i := 0; i < cap(p); i++ {
                p[i] = i + 1
        }
        return p
}

func print_div(p [100]int) int {
        for i := 0; i < cap(p); i++ {
                if p[i]%3 == 0 {
                        print(p[i], "\n")
                }
        }
        return 0
}

func main() {
        var array [100]int
        array = init_array(array)
        print_div(array)

}
vagrant@vagrant:~/go-lang$ go run Div3.go
3
6
9
12
15
18
21
24
27
30
33
36
39
42
45
48
51
54
57
60
63
66
69
72
75
78
81
84
87
90
93
96
99
```


В виде решения ссылку на код или сам код. 

## Задача 4. Протестировать код (не обязательно).

Создайте тесты для функций из предыдущего задания. 

---

### Как cдавать задание

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---

