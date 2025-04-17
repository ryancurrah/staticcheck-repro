# staticcheck-repro

This is a minimal reproduction of a bug in staticcheck that reports issues on code not in the repository.

The reproduction is a special case that is tripped by the following line.

```go
if iter := query.Run(input); iter != nil {
```

```console
❯ golangci-lint run ./...
../go/pkg/mod/github.com/itchyny/gojq@v0.12.14/query.go:24:17: SA4023(related information): (*github.com/itchyny/gojq.Query).Run never returns a nil interface value (staticcheck)
func (e *Query) Run(v any) Iter {
                ^
main.go:16:31: SA4023: this comparison is always true (staticcheck)
	if iter := query.Run(input); iter != nil {
	                             ^
2 issues:
* staticcheck: 2
```
