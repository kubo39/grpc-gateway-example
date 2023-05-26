# grpc-gateway-example

repository for grpc-gateway trial.

## Note

テストは[grpc-gatewayでgRPCとREST両対応のサーバを作る](https://future-architect.github.io/articles/20220624a/)ブログ記事のevansを使って確認する方法で行う。

ビルド時に proto/google/api 以下があるとこけるが、evansを使って動作確認する際にはこれらを要求するようになっている。たいへん不便であるが都度ディレクトリ作成・コピーを行う必要がある。

```console
$ make dev
docker-compose exec dev /bin/bash
root@e8b6a090214f:/work# evans --host grpc-server --port 50051 --path proto,include example/example.proto
evans: failed to run REPL mode: failed to instantiate a new spec: failed to instantiate the spec: proto: failed to parse passed proto files: example/example.proto:6:8: open proto/google/api/annotations.proto: no such file or directory
root@e8b6a090214f:/work#
exit
make: *** [Makefile:15: dev] Error 1
```

以下のファイルが必要

```console
cp googleapis/google/api/annotations.proto proto/google/api/
cp googleapis/google/api/http.proto proto/google/api/
```
