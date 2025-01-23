```go
/Пакет `os` в Go предоставляет интерфейсы и функции для работы с операционной системой.

os.Open(name string) (*os.File, error) /Открывает файл `name` для чтения
os.Create(name string) (*os.File, error) /Создает файл `name` или перезаписывает его, если он уже существует
os.Remove(name string) error /Удаляет файл или директорию `name`
os.Rename(oldpath, newpath string) error /Переименовывает файл или директорию
os.Stat(name string) (os.FileInfo. error) /Возвращает информацию о файле или директории

os.Getenv(key string) string /Возвращает значение переменной окружения `key`
os.Setenv(key, value string) error /Устанавливает значение переменной окружения `key` в `value`
os.Usetenv(key string) error /Удаляет переменную окружения `key`

os.Exit(code int) /Завершает выполнение программы  с кодом завершения `code`
os.StartProcess(name string, argv []string, attr *os.ProcAttr) (*os.Process, error) /Запускает новый процесс

os.Mkdir(name string, perm os.FileMode) error /Создает новую директорию с заданными правилами
os.Chdir(dir string) error /Изменяет текующую рабочую директорию на `dir`
os.Getwd() (string, error) /Возвращает текущую рабочую директорию

os.Stdin, os.Stdout, os.Stderr /Глобальные переменные, представляющие стандартные потоки ввода, вывода и ошибок
os.File /Структура, предоставляющая открытый файл, с методами чтения, записи и управления
```
