# w10_go_1

```bash
docker build -t dw11:0.1 .
docker run -p 80:80 dw11:0.1
docker run -p 80:80 dw11:0.1
git add .
git commit -m "update"
git push -u origin master 
go test
go test -v
go test -v -run TestFileServer
go test ./...
```