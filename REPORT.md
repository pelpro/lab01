# Лабораторная работа 01: #  

## Результаты прохождения туториала: ##

В результате прохождения туториала было создано пространство для пользователя pelpro(~/Git/pelpro/workspace)  на локальном компьюетере и настроена интеграция сервиса gist с локальным компьюntром.

## Домашнее задание: ##

1) Скачиваем wget-ом:  

wget  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
Результат:
Сохранение в: «boost_1_69_0.tar.gz.1»

boost_1_69_0.tar.gz 100%[===================>] 106,53M  5,07MB/s    за 25s     

2020-05-03 03:10:00 (4,19 MB/s) - «boost_1_69_0.tar.gz.1» сохранён [111710205/111710205]

2) Разархивируем в ~:

tar -xzvf boost_1_69_0.tar.gz.1 -C ~
P.S. verbose тут явно был лишний

3) Подсчет файлов в директории ~/boost_1_69_0 не включая вложенные директории.

find ~/boost_1_69_0/ -type f  -maxdepth 1 | wc -l 

12

4) Подсчет файлов в директории ~/boost_1_69_0 включая вложенные директории.  

find ~/boost_1_69_0/ -type f  | wc -l 

61191

5) Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).

find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l

13774

find ~/boost_1_69_0 -type f -name "*.h" | wc -l

296

find ~/boost_1_69_0 -type f -name "*.hpp" | wc -l

14912

find ~/boost_1_69_0 -type f -not -name "*.hpp" -not -name "*.cpp" -not -name "*.h" | wc -l

   33169

6) Полный путь до файла any.hpp внутри библиотеки boost:
find ~/boost_1_69_0 | grep boost/any.hpp

/Users/me/boost_1_69_0/boost/any.hpp

7)Выведите в консоль все файлы, где упоминается последовательность boost::asio.:

grep -rl "boost::asio" ~/boost_1_69_0


8) Компиляция boost:

./bootstrap.sh 

./b2


9) Перенос скомпилированных статических библиотек в директорию boost-libs:

mv ~/boost_1_69_0/stage/lib/ ~/boost-libs 

10) Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.

find ~/boost-libs/ type f -exec du -h {} +;

11) Найдите топ10 самых "тяжёлых".

find ~/boost-libs/ -exec du -h {} +| sort -rh | head -n 10 
245M	/Users/a17661665/boost-libs/
 45M	/Users/a17661665/boost-libs//libboost_wave.a
 26M	/Users/a17661665/boost-libs//libboost_log_setup.a
 22M	/Users/a17661665/boost-libs//libboost_log.a
 18M	/Users/a17661665/boost-libs//libboost_unit_test_framework.a
 18M	/Users/a17661665/boost-libs//libboost_test_exec_monitor.a
10,0M	/Users/a17661665/boost-libs//libboost_locale.a
9,8M	/Users/a17661665/boost-libs//libboost_regex.a
9,5M	/Users/a17661665/boost-libs//libboost_serialization.a
9,2M	/Users/a17661665/boost-libs//libboost_math_tr1f.a
