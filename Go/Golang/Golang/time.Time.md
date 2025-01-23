пакет - time

x.Sub(y) - разница во времени

```go
func TimeDifference(start, end time.Time) time.Duration {

    return start.Sub(end)

}
```

time.Time.Format(2006-01-02 15:04:05) etc

```go
func FormatTimeToString(timestamp time.Time, format string) string {
	now := timestamp
	return now.Format(format)
}
```

time.Parse(format, dateString) - парсит time.Time в string
time.Time{} - пустое значение для time.Time

```go
func ParseStringToTime(dateString, format string) (time.Time, error) {
    result, error := time.Parse(format, dateString)
    if error != nil {
        return time.Time{}, error
    }
    return result, nil
}
```

time.Since(x) - возвращает прошедшее с x время. Если указана будущая дата, то вывод отрицательный

```go
x.AddDate(years int, months int, days int)

futureTime := currentTime.AddDate(1, 2, 3)
```

