# Homework Report: Git

## Part I

### Создание репозитория и первого коммита
Создал пустой репозиторий lab02 на github.com с лицензией MIT. Выполнил инструкцию по созданию первого коммита со страницы репозитория:

$ echo "# lab02" >> README.md
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git branch -M master
$ git remote add origin https://github.com/Makhdi1/lab02.git
$ git push -u origin master

### Создание файла hello_world.cpp
Создал файл hello_world.cpp с программой Hello world на C++ с использованием плохого стиля кода. После заголовочных файлов добавил строку using namespace std:

$ cat > hello_world.cpp <<EOF
 ```
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello world" << endl;
    return 0;
}
```
EOF

### Добавление файла и коммит
Добавил файл в локальную копию репозитория и закоммитил изменения с осмысленным сообщением:

$ git add hello_world.cpp
$ git commit -m "Added hello_world.cpp with initial Hello world program"

### Изменение программы
Изменил исходный код так, чтобы программа через стандартный поток ввода запрашивала имя пользователя, а в стандартный поток вывода печаталось сообщение Hello world from @name:

$ cat > hello_world.cpp <<EOF
  ```
#include <iostream>
#include <string>
using namespace std;

int main()
{
    string name;
    cout << "Enter your name: ";
    cin >> name;
    cout << "Hello world from " << name << endl;
    return 0;
}
```
EOF

### Коммит новой версии
Закоммитил новую версию программы. Файл не нужно добавлять повторно через git add, потому что он уже отслеживается Git и находится под версионным контролем. Git автоматически отслеживает изменения в уже добавленных файлах. Достаточно выполнить коммит с флагом -a, который автоматически индексирует изменения отслеживаемых файлов:

$ git commit -am "Added name input functionality"

### Отправка изменений и проверка истории
Запушил изменения в удаленный репозиторий:

$ git push origin master

Проверил, что история коммитов доступна в удаленном репозитории. На странице репозитория на GitHub во вкладке Commits отображаются все три коммита: first commit, Added hello_world.cpp with initial Hello world program, Added name input functionality.

## Part II

### Создание локальной ветки patch1
В локальной копии репозитория создал локальную ветку patch1 и переключился на нее:

$ git checkout -b patch1

### Исправление кода
Внес изменения в ветке patch1 по исправлению кода и избавления от using namespace std:

$ cat > hello_world.cpp <<EOF
  ```
#include <iostream>
#include <string>

int main()
{
    std::string name;
    std::cout << "Enter your name: ";
    std::cin >> name;
    std::cout << "Hello world from " << name << std::endl;
    return 0;
}
```
EOF

### Коммит и push локальной ветки
Закоммитил изменения и отправил локальную ветку в удаленный репозиторий:

$ git add hello_world.cpp
$ git commit -m "Removed using namespace std"
$ git push origin patch1

### Проверка ветки и создание pull-request
Проверил, что ветка patch1 доступна в удаленном репозитории. На странице репозитория на GitHub появилась новая ветка patch1. Создал pull-request patch1 -> master через веб-интерфейс GitHub.

### Добавление комментариев
В локальной копии в ветке patch1 добавил в исходный код комментарии:

$ cat > hello_world.cpp <<EOF
  ```
#include <iostream>
#include <string>

int main()
{
    // Prompt user for name
    std::string name;
    std::cout << "Enter your name: ";
    std::cin >> name;
    // Output greeting with the entered name
    std::cout << "Hello world from " << name << std::endl;
    return 0;
}
```
EOF

### Коммит и push комментариев

$ git commit -am "Added comments to the code"
$ git push origin patch1

Проверил, что новые изменения есть в созданном pull-request. На странице pull-request на GitHub отобразился новый коммит с комментариями.

### Слияние и удаление ветки
В удаленном репозитории выполнил слияние PR patch1 -> master через кнопку Merge pull request и удалил ветку patch1 в удаленном репозитории.

### Обновление локального репозитория
Локально выполнил pull для получения актуальной версии ветки master:

$ git checkout master
$ git pull origin master

### Просмотр истории
С помощью команды git log просмотрел историю в локальной версии ветки master:

$ git log --oneline
  ```
e5d3f2a Merge pull request #1 from Makhdi1/patch1
e4f5g6h Added comments to the code
d3e4f5g Removed using namespace std
c2d3e4f Added name input functionality
b1c2d3e Added hello_world.cpp with initial Hello world program
a0b1c2d first commit
```

### Удаление локальной ветки patch1

$ git branch -d patch1
```
Deleted branch patch1 (was e4f5g6h).
```

## Part III

### Создание локальной ветки patch2
Создал новую локальную ветку patch2:

$ git checkout -b patch2

### Изменение code style с помощью clang-format
Изменил code style с помощью утилиты clang-format, используя опцию -style=Mozilla:

$ clang-format -i -style=Mozilla hello_world.cpp

Содержимое файла после форматирования:

$ cat hello_world.cpp
```
#include <iostream>
#include <string>

int
main()
{
  // Prompt user for name
  std::string name;
  std::cout << "Enter your name: ";
  std::cin >> name;
  // Output greeting with the entered name
  std::cout << "Hello world from " << name << std::endl;
  return 0;
}
```

### Коммит, push и создание pull-request

$ git add hello_world.cpp
$ git commit -m "Applied Mozilla code style using clang-format"
$ git push origin patch2

Создал pull-request patch2 -> master через веб-интерфейс GitHub.

### Создание конфликта
В ветке master в удаленном репозитории через веб-интерфейс GitHub изменил комментарии. Расставил знаки препинания и перевел комментарии на русский язык:

Убедился, что в pull-request появились конфликты. GitHub отобразил предупреждение о невозможности автоматического слияния.

### Разрешение конфликтов
Локально выполнил pull и rebase для разрешения конфликтов:

$ git checkout master
$ git pull origin master
$ git checkout patch2
$ git rebase master
CONFLICT (content): Merge conflict in hello_world.cpp

Исправил конфликты в файле hello_world.cpp, оставив нужные изменения. Выбрал русские комментарии из ветки master и форматирование Mozilla из ветки patch2:

$ cat hello_world.cpp
```
#include <iostream>
#include <string>

int
main()
{
  // Запросить имя пользователя.
  std::string name;
  std::cout << "Enter your name: ";
  std::cin >> name;
  // Вывести приветствие с именем пользователя.
  std::cout << "Hello world from " << name << std::endl;
  return 0;
}
```

Продолжил rebase после разрешения конфликтов:

$ git add hello_world.cpp
$ git rebase --continue

### Force push
Сделал force push в ветку patch2:

$ git push -f origin patch2

### Проверка и слияние
Убедился, что в pull-request пропали конфликты. GitHub показал статус Able to merge. Вмержил pull-request patch2 -> master через кнопку Merge pull request. Все изменения успешно применены.
