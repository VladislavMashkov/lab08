[![Build Status](https://travis-ci.org/VladislavMashkov/lab08.svg?branch=master)](https://travis-ci.org/VladislavMashkov/lab08)
## Laboratory work III
Машков Владислав ИУ8-33
Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [X] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [X] 2. Ознакомиться со ссылками учебного материала
- [X] 3. Выполнить инструкцию учебного материала
- [X] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
# Устанавливаем значение переменной окружения GITHUB_USERNAME
$ export GITHUB_USERNAME=VladislavMashkov
# Устанавливаем значение переменной окружения GITHUB_EMAIL
$ export GITHUB_EMAIL=Vlad_mashkow@mail.ru
# Создаем алиас на редактирование файлов редактором atom(то есть создаем альтернативную
#версию команды edit)
$ alias edit=atom
```

```ShellSession
# Создаем директорию lab03 и переходим в нее
$ mkdir lab03 && cd lab03
# Создаем репозиторий Git
$ git init
# Устанавливаем глобальные параметры
# user.name
$ git config --global user.name ${GITHUB_USERNAME}
# user.email
$ git config --global user.email ${GITHUB_EMAIL}
# Открываем файл конфигураций и наблюдаем за правильностью
# Введеных нами глобальных параметров
$ git config -e --global
# Добавляем удаленный репозиторий по ссылке
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03
# Копируем содержимое удаленного репозитория в локальный
$ git pull origin master
# Создаем файл README.MD
$ touch README.md
# Отображаем неподтвержденные и подтверждения файлы в репозиториях
$ git status
# Добавляем README.md в подтвержденные, то есть подтверждаем изменения
# В README.md на удаленном репозитории
$ git add README.md
# Сопровождаем отправку файла в удаленный репозиторий сообщением
# И сохраняем изменения на удаленном репозитории
$ git commit -m"added README.md"
$ git push origin master
```

Добавить на сервисе **GitHub** в репозитории **lab03** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
```

```ShellSession
# Копируем содержимое удаленного репозитория в локальный
# В том числе копируется .gitignore
$ git pull origin master
# Отображает журнал всех изменений
$ git log
```

```ShellSession
# Создаем каталоги sources, include, examples
$ mkdir sources
$ mkdir include
$ mkdir examples
# Создаем файлыи добавляем в них код
$ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {
  out << text;
}
EOF
```

```ShellSession
$ cat > include/print.hpp <<EOF
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);
EOF
```

```ShellSession
$ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF
```

```ShellSession
$ cat > examples/example2.cpp <<EOF
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```

```ShellSession
$ edit README.md
```

```ShellSession
$ git status
$ git add .
$ git commit -m"added sources"
$ git push origin master
```

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=03
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2017 Братья Вершинины
```
