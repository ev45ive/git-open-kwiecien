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

git config --unset user.placki 
git config --unset user.placki 