```go
import "strings"

strings.Builder - структура, позволяющая накапливать данные в виде строки через вызовы без создания промежуточных копий.

Основные методы strings.Builder:
	WriteString(s string) (int, error) - доблавяет строку в буфер
	WriteRune(r rune) (int, error) - добавляет один символ в буфер
	Write(b []byte) (int, error) - добавляет байты в буфер
	String() string - возвращает строку
	Reset() - очищает буфер
	Len() int - возвращет длину накопленной строки
```