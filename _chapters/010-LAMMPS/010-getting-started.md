---
title: Установка LAMMPS
slug: install LAMMPS
abstract: LAMMPS - один из главных тяжеловесов в мире МД, который за тридцать лет разработки вобрал в себя практически всё, что вам может понадобиться для классического атомистического моделирования. Комьюнити пользователей тоже огромное, а значит любой баг, который вы поймаете, кто-то уже обсуждал [на официальном форуме](https://www.lammps.org/forum.html) N лет назад и найти решение будет несложно. LAMMPS бесплатный, он open-sorce и он отлично параллелится даже на самых крупных суперкомпьютерах.
---

Если вы скачали нашу [виртуальную машину](https://mdcrashcourse.github.io/vm.html), эту главу можно пропустить - на ней уже всё установлено.

**Disclaimer**: если вы биохимик и вас интересуют белки, мембраны и прочая биоорганика, возможно, LAMMPS для вас не самый оптимальный выбор. Рекомендуем заглянуть в главы про [Gromacs](https://mdcrashcourse.github.io/gromacs.html) и [OpenMM](https://mdcrashcourse.github.io/gromacs.html).

---
## Где скачать?

- C официального сайта: [`www.lammps.org/download.html`](www.lammps.org/download.html) (возможны проблемы при доступе с российских IP). Выбираем `LAMMPS Stable release`.
  

- Из официального репозитория на **github**: [`https://github.com/lammps/lammps`](https://github.com/lammps/lammps)


```liquid
git clone -b stable https://github.com/lammps/lammps.git lammps23
```
команда создаст директорию **lammps23** и скачает туда актуальную версию. Если система не видит команду **git**, значит его надо установить:
```liquid
sudo apt-get install git
```
---

## Компиляция

- Обновляем данные о репозитории, устанавливаем **make** и [**MPI**](https://en.wikipedia.org/wiki/Message_Passing_Interface), если их еще нет:

```liquid
sudo apt-get update             
sudo apt-get install make			        
sudo apt-get install mpich   
```


- Переходим в папку с исходниками `src`, включаем, если надо, дополнительные модули (`make yes-REAXFF`) и компилируем *многопоточную*, то есть использующую для расчетов сразу несколько ядер, версию (`make mpi`). Если *многопоточная* версия нам не нужна или с ней что-то не ладится, то для тестов можно скомпилировать *однопоточную* версию, заменив `make mpi` на `make serial`:

```liquid
cd lammps23/src
make yes-REAXFF
make mpi
```

Подробная информация в мануалах: [`https://docs.lammps.org/Build_make.html`](https://docs.lammps.org/Build_make.html) и [`https://docs.lammps.org/Install.html`](https://docs.lammps.org/Install.html). Если не открывается, можно попробовать [`зеркало`](https://guriang.unpad.ac.id/hpc/lammpsdoc/Manual.html), но там не самая свежая версия (30 Jul 2021).


---

## Пример установки

[**Презентация**](https://github.com/mdcrashcourse/course_data/blob/main/1_Lammps/presentation/Lammps_intro2024.pptx) из видео.


{% include youtube.html id="ypzUOF0yZuY" %}

---

{% include youtube.html id="5h4x6rzd2nE" %}




---
    
