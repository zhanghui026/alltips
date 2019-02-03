#  SHELL Tips

## 查看日志

* 行数计数

> find fabric -name "*.go" -not -path "fabric/vendor/*" | xargs cat | wc -l

