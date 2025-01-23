```go
/С использованием make
m := make(map[type]type)
/С помощью литералов
m := map[type]type{"x" : y, ...}
/Добавление или обновление значения
m["key_name"] = value
/ Чтение значения
val := m["key_name"]
/Проверка существования ключа
val, exist := m["key_name"]
if exist{
	fmt.Println("Key exists:", val)
} else {
	fmt.Println("Key does not exist")
}
/Удаление ключа
delete(m, "key_name")
/
```