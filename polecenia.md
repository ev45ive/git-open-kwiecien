Visual Studio https://code.visualstudio.com/
Git Bash https://git-scm.com/download/win

## Visual 
File > Open Folder
Create New Folder "git-open-kwiecien"
Wybierz folder
Terminal -> New Terminal (Ctrl+`)

## GIT 
$ git status
fatal: not a git repository (or any of the parent directories): .git

## Init - tworzenie nowego repozytorium
git init nazwakatalogu
git init .

git init

Initialized empty Git repository in C:/Projects/szkolenia/git-open-kwiecien/.git/
ls -a

## status - sprawdzamy stan
git status

# Tworzymy plik


## Index (poczekalnia) - lista plików do Commitu (migawki)
git add nazwapliku.txt
<!-- git status - nazwapliku.txt -- na zielono! - W poczekalni! -->
git add nazwapliku2.txt
<!-- dodajemy caly katalog bieżący do poczekalni -->
git add . 

## Commit
git commit 

Author identity unknown
*** Please tell me who you are.
Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'PC@DESKTOP-6HIPUQN.(none)')

## Config
git config --list
<!-- Kaskada - lokalne nadpisuja globalne, globlne nadpisuja wbudowane -->
<!-- katalogprojektu/.git/gitconfig -->

git config user.name "Zbyszek"
git config --unset user.name 

## Config globalny
C:\Users\<nazwa usera>\.gitconfig
git config --global user.email "mateusz@altkomakademia.pl"
git config --global --unset user.email


git config --global user.email "mateusz@altkomakademia.pl"
git config --global user.name "Mateusz Kulesza"
git config --list --global

cat ~/.gitconfig 
<!-- [user]
        email = mateusz@altkomakademia.pl
        name = Mateusz Kulesza -->

## Commit + message (VIM)
git commit 
<!-- Wychodzenie bez zmian-->
ESC :q ENTER - Quit 
<!-- Aborting commit due to empty commit message.  -->
<!-- Wprowadzanie tekstu -->
ESC a 
<!-- Wychodzenie bez zapisywania zmian -->
ESC :q! ENTER - Quit 
<!-- Zapis i commit  -->
ESC :wq ENTER
<!-- Write + Quit -->

## Log - przeglad historii
git log

## Diff - podglad zmian
git diff HEAD 25c5732
git diff HEAD master~1
git diff HEAD master~1 test.txt
git diff 63ed94aa test.txt

## Restore - wycofaj lokalne zmiany (tracimy niezpisane zmiany !!!)
git restore plik_z_niepotrzebnymi_zmainami.txt

## Show - podglad okreslonego commita
git show master
git show master~3
git show 9bf011ff

## Checkout - wyciagnij stara wersje pliku
git checkout 63ed94aa test.txt
git checkout 63ed94aa test.txt innyplik.txt

## Git commit --amend
git commit --amend -m "Strona o GIT - plik index"
<!-- New commit, new hash -->
git add .
git commit --amend --no-edit

## Changing commits - kazda zmiana tworzy nowy unikalny commit id
git show --format="fuller" 46164767

commit 461647677e92b1c1532714f2eeb7c7e8aa7b37a1 (HEAD -> master)
Author:     Mateusz Kulesza <mateusz@altkomakademia.pl>
AuthorDate: Thu Apr 22 13:36:05 2021 +0200
Commit:     Mateusz Kulesza <mateusz@altkomakademia.pl>
CommitDate: Thu Apr 22 13:45:01 2021 +0200

## Git files - rm, mv, .gitignore, .gitkeep
Commit file operations 

## Git internals - plumbing - nie rób tego w domu!
git hash-object test.txt  > 30d74d258442c7c65512eafab474568dd706c430

git hash-object -w test.txt
git cat-file -p 30d74d258442c7c65512eafab474568dd706c430 > test.txt

git update-index --add --cacheinfo 100644 30d74d258442c7c65512eafab474568dd706c430 test.txt
git write-tree
3b6d230f2feef161a7cd34900cc63f900ba211b3

git update-index --add --cacheinfo 100644 30d74d258442c7c65512eafab474568dd706c430 test2.txt
git write-tree
b2be2734095c5d869ab0fe2fe41f9068040c1d27

git read-tree --prefix=podkatalog b2be2734095c5d869ab0fe2fe41f9068040c1d27
 git write-tree
95bfd5df30043c8931fa9ff9c0fc2ec74851025a
git cat-file -p 95bfd5df30043c8931fa9ff9c0fc2ec74851025a
040000 tree b2be2734095c5d869ab0fe2fe41f9068040c1d27    podkatalog
100644 blob 30d74d258442c7c65512eafab474568dd706c430    test.txt  

git commit-tree 95bfd5df30043c8931fa9ff9c0fc2ec74851025a -m "first commit"
b7a7609793568befb616c079e1de65118229128d


git update-index --add --cacheinfo 100644 30d74d258442c7c65512eafab474568dd706c430 test123.txt  
git write-tree
787d3dc126efcc69ede7c31dd7967367181f9879

git commit-tree 787d3dc126efcc69ede7c31dd7967367181f9879 -m "second commit" -p b7a7609793568befb616c079e1de65118229128d
3d0bb4a7dcc1fdd704bea1e8bd0a14642b6a852a

git cat-file -p 3d0bb4a7dcc1fdd704bea1e8bd0a14642b6a852a
tree 787d3dc126efcc69ede7c31dd7967367181f9879
parent b7a7609793568befb616c079e1de65118229128d
author Mateusz Kulesza <mateusz@altkomakademia.pl> 1619095425 +0200
committer Mateusz Kulesza <mateusz@altkomakademia.pl> 1619095425 +0200

second commit

git log

