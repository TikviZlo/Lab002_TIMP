en
### Part I

## 1. Создайте пустой репозиторий на сервисе github.com.

```
$ cd ~/inna/Документы/ГитПроекты
$ mkdir Lab002
$ cd Lab002
$ git init
$ git config --global user.name ${GITHUB_USERNAME}
$ git config --global user.email ${GITHUB_EMAIL}
$ git remote add origin https://github.com/TikviZlo/TIMP_Lab002.git
$ git pull origin master
$ touch LabReport002.md
$ git status
$ git add LabReport002.md
$ git commit -m"Добавила отчёт"
$ git push origin main
```

## 2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.

Создаём файл .gitignore

```

$ cat .gitignore  <<EOF
*build*/ 
*install*/
*.swp
.idea/
EO
```

Загружаем его на GitHub
    
```
$ git add .gitignore
$ git commit -m"Создала гитигнор"
$ git push origin main
```

## 3. Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.

```
$ cat > hello_world.cpp <<EOF
#include <iostream>
using namespace std;
int main(){cout << "Hello world" << endl; return 0;}
EOF
```

## 4. Добавьте этот файл в локальную копию репозитория.

```
$ git add hello_world.cpp
```

## 5. Закоммитьте изменения с осмысленным сообщением.

```
$ git commit -m"Осмысленное сообщение"
```

## 6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.

```
$ cat > hello_world.cpp <<EOF
#include <iostream>
#include <string>
using namespace std;
int main(){string name;cout << "Type your name: ";cin >> name;cout << "Hello world and " << name << endl; return 0;}
EOF
```

## 7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?

```
$ git commit hello_world.cpp -m"Changed hello_world.cpp"
```

Т.к. мы не загрузили файл на GitHub и фактически продолжаем с ним работать, то можно обойтись без повторного использования git add


## 8. Запуште изменения в удалёный репозиторий.

```
$ git push origin master
```

## 9. Проверьте, что история коммитов доступна в удалёный репозитории.

#### Part II

Note: Работать продолжайте с теми же репоззиториями, что и в первой части задания.

## 1. В локальной копии репозитория создайте локальную ветку patch1.

```
$ git branch patch1
$ git switch patch1

```

## 2. Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.

```
$ cat > helloworld.cpp <<EOF
#include <iostream>
#include <string>

int main()
{
    std::string name;
    std::cout << "Type your name: ";
    std::cin >> name;
    std::cout << "Hello world and " << name << std::endl;
    return 0;
}

EOF
```

## 3. commit, push локальную ветку в удалённый репозиторий.

```
$ git commit -m"Ветка 1"
$ git push origin patch1
```

## 4. Проверьте, что ветка patch1 доступна в удалёный репозитории.

## 5. Создайте pull-request patch1 -> master.

## 6. В локальной копии в ветке patch1 добавьте в исходный код комментарии.

```
$ cat > helloworld.cpp <<EOF
#include <iostream>
#include <string>

int main(int argc, char** argv)
{
    std::string name; // Инициальзируем переменную name типа string
    std::cout << "Type your name: "; // Просим ввести имя пользователя
    std::cin >> name; // Запрашиваем значение переменной name из потока ввода вывода
    std::cout << "Hello world and " << name << std::endl; // Выводим преветствие
    return 0;
}

EOF
```

## 7. commit, push.

```
$ git push origin patch1
```

## 8. Проверьте, что новые изменения есть в созданном на шаге 5 pull-request

## 9. В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.

## 10. Локально выполните pull.

```
$ git pull origin main
```

## 11. С помощью команды git log просмотрите историю в локальной версии ветки master.

```
$ git log


commit 483426cb6169ece20492c6428b3cb152bc3edbdd (HEAD -> main, origin/main, origin/HEAD)
Merge: da9d8f1 88e3b23
Author: TikviZlo <99878768+TikviZlo@users.noreply.github.com>
Date:   Sun Sep 11 17:06:17 2022 +0300

    Merge pull request #1 from TikviZlo/patch1

    Ветка 1

commit 88e3b2338e067aeefdb20d2918bea0e8e916f8c4 (patch1)
Author: TikviZlo <99878768+TikviZlo@users.noreply.github.com>
Date:   Sun Sep 11 17:01:19 2022 +0300

    добавила комментарии к коду

commit 49741af1340973d2cbd6d361aa89928dcb639e34
Author: TikviZlo <99878768+TikviZlo@users.noreply.github.com>
Date:   Sun Sep 11 12:40:43 2022 +0300

    Ветка 1

commit da9d8f15d3bf1ff1d672a8b56142a07a95b6b27f
:
```

## 12. Удалите локальную ветку patch1.
```
$ git branch -d patch1
```
### Part III

Note: Работать продолжайте с теми же репоззиториями, что и в первой части задания.

## 1. Создайте новую локальную ветку patch2.

```
$ git branch patch2
$ git 
$ git clone https://github.com/TikviZlo/TIMP_Lab002.git -b main
```

## 2. Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.

```
$ clang-format -style=Mozilla -i ./sources/hello_world.cpp
```

## 3. commit, push, создайте pull-request patch2 -> master.

```
$ git commit -m"Ветка 2"
$ git push origin patch2
```

<details>

<summary>Вывод комманды:</summary>

Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'patch2' on GitHub by visiting:
remote:      https://github.com/TikviZlo/TIMP_Lab002/pull/new/patch2
remote:
To https://github.com/TikviZlo/TIMP_Lab002.git
 * [new branch]      patch2 -> patch2

</details>

## 4. В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
 
## 5. Убедитесь, что в pull-request появились конфликты.

## 6. Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.

```
$ git switch main
$ git pull origin main
$ git switch patch2
$ git add hello_world.cpp
$ git rebase main
$ git rebase --continue
```

## 7. Сделайте force push в ветку patch2

```
$ git push -f origin patch2
```

## 8. Убедитель, что в pull-request пропали конфликтны.

## 9. Вмержите pull-request patch2 -> master.
