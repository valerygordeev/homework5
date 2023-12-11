# homework5
1  Входим как root sudo su
2  Просмотр устройств lsblk
3  Создание 4 raid mirror массивов по 2 устройства в каждом
   zpool create [наименование] mirror /dev/sdb /dev/sdc
   далее пары sdd/sde, sdf/sdg, sdh/sdi
4  Просматриваем информацию о дисках zpool list
5  Добавим алгоритмы сжатия на файловые сисемы дисков
   zfs set compression=lzjb otus1
   zfs set compression=lz4 otus2
   zfs set compression=gzip-9 otus3
   zfs set compression=zle otus4
6  Проверим установку алгоритмов сжатия zfs get all | grep compression
7  Для проверки сжатия скачаем файл на все диски
   for i in {1..4}; do wget -P /otus$i https://gutenberg.org/cache/epub/2600/pg2600.converter.log; done
8  Коэфициенты сжатия отображаются по команде zfs list
9  Просмотр всех параметров файловой системы otus
   zfs get all otus
10 Определение доступного места zfs get available utus
11 Определение возможности записи zfs get readonly otus
12 Определяем размер блока zfs get recordsize otus
13 Алгоритм сжатия zfs get compression otus
14 Определение включения подсчета контрольной суммы и ее алгоритма
   zfs get checksum otus
15 Работа с snapshot.
   Скачиваем файл snapshot
   wget -O otus_task2.file --no-check-certificate https://drive.usercontent.google.com/download?id=1wgxjih8YZ-cqLqaZVa0lA3h3Y029c3oI&export=download
   Восстановим файловую систему по полученному файлу
   zfs receive otus/test@today < otus_task2.file
16 Поиск файла в директории otus/test по имени
   find /otus/test -name "secret_message"
17 Просмотр содержания найденного файла
   cat /otus/test/task1/file_mess/secret_message

   Ссылка на курс https://otus.ru/lessons/linux-hl/

