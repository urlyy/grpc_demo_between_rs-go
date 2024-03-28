# 介绍
一个go与rust使用gprc、protobuf进行数据通信的示例

# 运行
1. 下载protoc，并配置环境变量[https://github.com/protocolbuffers/protobuf/releases](https://github.com/protocolbuffers/protobuf/releases)
2. 生成go的pb文件
   ```shell
   cd go-client/rpc
   mkdir pkg
   protoc --go_out=./pkg/ --go-grpc_out=./pkg/  proto/hello.proto
   ```
3. 启动服务端
```shell
cd rust-server
cargo run
```
4. 客户端发送一次信息
打开新终端
```shell
cd go-client
go mod tidy
go run main.go
```


- 您可以自己配置server的端口以及proto文件，注意go那里的proto文件的第二行是导出的package和文件夹名


# 参考教程
- rust作为server，rpc使用tonic框架
[官方教程](https://github.com/hyperium/tonic/blob/master/examples/helloworld-tutorial.md)

- go作为service，使用grpc
[go语言使用grpc](https://blog.csdn.net/qq_45716329/article/details/129207604?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171043359016800211582970%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171043359016800211582970&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-129207604-null-null.142%5Ev99%5Epc_search_result_base9&utm_term=go%E4%BD%BF%E7%94%A8grpc&spm=1018.2226.3001.4187)