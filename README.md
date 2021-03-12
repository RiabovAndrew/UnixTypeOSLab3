# UnixTypeOSLab3

## Отчёт по лабораторной работе №3   

по дисциплине "Unix-подобные операционные системы"   
студента группы ПА-18-2   
Рябова Андрея Дмитриевича   
Кафедра Компьютерных Технологий ДНУ 2021/2022

### Постановка задачи:   

![image](https://user-images.githubusercontent.com/43186510/110943421-db496580-8343-11eb-90c4-12ed103d6119.png)

### Выполнение:   

#### 1. Bash skript

Напишем простой bash скрипт, который принимает один аргумент - имя, и возвращает его.

![image](https://user-images.githubusercontent.com/43186510/110944394-14360a00-8345-11eb-9093-322cb9c2cae0.png)

Команды: `cmod -x ./1.bash` и `bash 1.bash`

![image](https://user-images.githubusercontent.com/43186510/110944428-20ba6280-8345-11eb-94c5-83c6ef3d75e6.png)

#### 2. Написать программу на С

##### 2.1. Язык С

Команды: `gcc file.c` и `./a.out`

Выполнение:   
![image](https://user-images.githubusercontent.com/43186510/110945189-1187e480-8346-11eb-8caf-3f34dcd2dcd8.png)

```
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>

int fibo(const int number) {
  return number < 2 ? number : fibo(number - 1) + fibo(number - 2);
}

int main(const int argc, char* argv[]) {
  if(argc < 2) {
    printf("Not enough arguments!\n");
  }
  else {
    char* error;
    const int number = strtol(argv[1], &error, 10);
    if (*error != 0 && !isspace((unsigned char)*error) || number < 0) {
      printf("Argument error!\n");
    }
    else {
      printf("Fibo(%i) result: %i\n", number, fibo(number));
    }
  }
  return 0;
}
```

##### 2.2. Язык С#

Команды: `mcs file.cs` и `mono file.exe`

Выполнение:   
![image](https://user-images.githubusercontent.com/43186510/110945509-704d5e00-8346-11eb-8aed-7ffb3c99c2f3.png)

```
using System;

namespace UnixTypeLab3 {
    class Program {
        public static uint Fibo(uint number) { return number < 2 ? number : Fibo(number - 1) + Fibo(number - 2); }

        static void Main(string[] args) {
            if (args.Length < 1) {
                Console.WriteLine("Not enough arguments\n");
            }
            else {
                uint number;
                if (!uint.TryParse(args[0], out number)) {
                    Console.WriteLine("Argument error\n");
                }
                else {
                    Console.WriteLine($"Fibo({number}) result: {Fibo(number)}");
                }
            }
        }
    }
}
```


##### 2.2. Язык Python

Команды: `python3 file.py`

Выполнение:   
![image](https://user-images.githubusercontent.com/43186510/110945654-a38fed00-8346-11eb-8623-07ff4b96c6fe.png)

```
import sys


def fibo(number):
    return number if number < 2 else fibo(number - 1) + fibo(number - 2)


if __name__ == "__main__":
    if len(sys.argv) < 2:
        print("Not enough arguments")
    else:
        if not sys.argv[1].isdecimal() or (int(sys.argv[1]) < 0 if str(sys.argv[1]).isdigit() else False):
            print("Argument arror")
        else:
            print("Fibo({}) result: {}".format(sys.argv[1], fibo(int(sys.argv[1]))))
```

##### 2.2. Язык PHP

Команды: `php file.php`

Выполнение:   
![image](https://user-images.githubusercontent.com/43186510/110945753-c3bfac00-8346-11eb-8806-049e0161f613.png)

```
<?php

function fibo($number) {
    return $number < 2 ? $number : fibo($number - 1) + fibo($number - 2);
}

if ($argc < 2) {
    echo "Not enough arguments\n";
}
else {
    if (intval($argv[1]) == 0 or $argv[1] != strval(intval($argv[1])) or intval($argv[1]) < 0) {
        echo "Argument error\n";
    }
    else {
        echo sprintf("Fibo(%d) result: %d\n", intval($argv[1]), fibo(intval($argv[1])));
    }
}
```

#### 3. Установка компиляторf псс

Установим компилятор командой  `$ sudo apt install build-essential`

После ввода пароля получим сообщение:

![image](https://user-images.githubusercontent.com/43186510/110946397-7b54be00-8347-11eb-8ddb-876ecdde812e.png)

Это говорит о полной установке gcc компилятора. Его работу показано выше в пункте 2.
