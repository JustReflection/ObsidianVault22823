### io.Reader
```go
//Интерфейс io.Reader используется для чтения данных из различных источников (файлов, сетевых соединений, буферов и т.д.). Это один из базовых интерфейсов в пакете io, который позволяет абстрагировать процесс чтения данных.

//Определение интерфейса io.Reader
type Reader interface{
	Read([]p byte) (n int, err error)
}

reader := strings.NewReader("Hello, Go!")
buf := make([]byte, 4)
for {
	n, err := reader.Read(buf)
	if err == io.EOF{
		break
	} else if err != nil{
		fmt.Println("Error reading:", err)
		return
	}
	fmt.Printf("Read %d bytes: %s\n", n, buf[:n])
}

//Создае объект, реализующий интерфейс io.Reader для чтения данных из строки.
func NewReader(s string) *strings.Reader

reader := strings.NewReader("Hello, Go!")
fmt.Println("Осталось байт для чтения:", reader.Len())

fmt.Println("Размер строки:", reader.Size())

//Перемещение указателя чтения на новую позицию
Seek(offset int64, whence int)
//Whence принимает значение:
io.SeekStart(0) //Начало строки
io.SeekCurrent(1) //От текущей позиции
io.SeekEnd(2) //От конца строки

reader := strings.NewReader("Go is awesome!")
reader.Seek(3, io.SeekStart) //Переместить указатель на 4 символ
buf := make([]byte, 7)
n, _ := reader.Read(buf)
fmt.Printf("Прочитано %d байт: %s\n", n, buf)

//Читает данные из строки, начиная с определенного смещения
ReadAt(p []byte, off int64)

//Копирует данные из одного io.Reader в io.Writer

func Copy(dst Writer, src Reader) (written int64, err error)
file, _ := os.Open("file.text")
defer file.Close()
io.Copy(os.Stdout, file)

//Копирует ровно n байт

func CopyN(dst Writer, src Reader, n int64) (written int64, err error)
io.CopyN(os.Stdout, file, 10)

//Читает все данные из Reader и возвращает их в виде среза байт

func ReadAll(r Reader) ([]byte, error)
data, err := io.ReadAll(file)
if err != nil{
	fmt.Println("Error:", err)
}
fmt.Println(string(data))

//Возвращает Reader, который читает из исходного Reader, но ограничивает количество байт

func LimitReader(r Reader, n int64) Reader
limited := io.LimitReader(file, 100)

//Создает bufio.Reader для буферизованного чтения. Чтение данных небольшими порциями

func NewReader(rd io.Reader) *Reader
reader := bufio.NewReader(file)
line, _, _ := reader.ReadLine()
fmt.Println(string(file))

//Читает данные из Reader и записивает их в Writer, обратно передавая как Reader

func TeeReader(r Reader, w Writer) Reader
file, _ := os.Open("file.txt")
tee := io.TeeReader(file, os.Stdout)
io.ReadAll(tee)
```

### io.Writer
```go
//Интерфейс io.Writer предоставляет способ записи байтов в различные источники, поддерживающие запись.

type Writer interface{
	Write(p []byte) (n int, err error)
}
func main() {
    // Открываем файл для записи
    file, err := os.Create("example.txt")
    if err != nil {
        fmt.Println("Ошибка создания файла:", err)
        return
    }
    defer file.Close()
    // Записываем строку в файл через io.Writer
    data := "Hello, Go!"
    if _, err := writeToFile(file, data); err != nil {
        fmt.Println("Ошибка записи:", err)
    } else {
        fmt.Println("Данные успешно записаны!")
    }
}
// Функция записи данных с использованием интерфейса io.Writer
func writeToFile(w io.Writer, data string) (int, error) {
    return w.Write([]byte(data))
}

```