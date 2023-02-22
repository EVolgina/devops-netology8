## Задание
# Какого типа команда cd? Попробуйте объяснить, почему она именно такого типа: опишите ход своих мыслей, если считаете, что она могла бы быть другого типа.
ответ: 
$ type cd
cd is a shell builtin
сd во всех случаях является встроенной командой, так как смена текущей директории в рамках дочернего процесса не приведет ни к каким последствиям на уровне командной оболочки. Смена текущей директории в рамках дочерней командной оболочки также не влияет на текущую директорию родительской командной оболочки

# Какая альтернатива без pipe команде grep <some_string> <some_file> | wc -l?\
Подсказка: man grep поможет в ответе на этот вопрос.
ответ: wc -l < <(<some_string> <some_file>)

Ознакомьтесь с документом о других подобных некорректных вариантах использования pipe.
# Какой процесс с PID 1 является родителем для всех процессов в вашей виртуальной машине Ubuntu 20.04?
ps (processes status — статус процессов) 
Команда pstree отображает запущенные процессы в виде древовидной структуры
Для каждого процесса создается каталог по пути /proc/<PID>, в котором создаются папки и файлы с описанием процесса.
Символьная ссылка на исполняемый файл, запустивший процесс: ll /proc/<PID>/exe


# Как будет выглядеть команда, которая перенаправит вывод stderr ls на другую сессию терминала?

# Получится ли одновременно передать команде файл на stdin и вывести ее stdout в другой файл? Приведите работающий пример.

# Получится ли, находясь в графическом режиме, вывести данные из PTY в какой-либо из эмуляторов TTY? Сможете ли вы наблюдать выводимые данные?

# Выполните команду bash 5>&1. К чему она приведет? Что будет, если вы выполните echo netology > /proc/$$/fd/5? Почему так происходит?

# Получится ли в качестве входного потока для pipe использовать только stderr команды, не потеряв при этом отображение stdout на pty?
Напоминаем: по умолчанию через pipe передается только stdout команды слева от | на stdin команды справа. Это можно сделать,\
поменяв стандартные потоки местами через промежуточный новый дескриптор, который вы научились создавать в предыдущем вопросе.

# Что выведет команда cat /proc/$$/environ? Как еще можно получить аналогичный по содержанию вывод?

# Используя man, опишите что доступно по адресам /proc/<PID>/cmdline, /proc/<PID>/exe.

# Узнайте, какую наиболее старшую версию набора инструкций SSE поддерживает ваш процессор с помощью /proc/cpuinfo.

# При открытии нового окна терминала и vagrant ssh создается новая сессия и выделяется pty.
Это можно подтвердить командой tty, которая упоминалась в лекции 3.2.\
Однако: vagrant@netology1:~$ ssh localhost 'tty'\
not a tty
Почитайте, почему так происходит, и как изменить поведение.

# Бывает, что есть необходимость переместить запущенный процесс из одной сессии в другую. Попробуйте сделать это, воспользовавшись reptyr. 
Например, так можно перенести в screen процесс, который вы запустили по ошибке в обычной SSH-сессии.

sudo echo string > /root/new_file не даст выполнить перенаправление под обычным пользователем, так как перенаправлением занимается процесс shell'а, который запущен без sudo под вашим пользователем. Для решения данной проблемы можно использовать конструкцию echo string | sudo tee /root/new_file. Узнайте? что делает команда tee и почему в отличие от sudo echo команда с sudo tee будет работать.


