### GO のビルドタグを試す

#### ビルド

以下のようにファイルの先頭にビルドタグを記述する。

```
//go:build en
```

#### ビルド

ビルド時に `-tags` オプションを指定することで、ビルドタグを有効にすることができる。

- `go build -tags jp main.go` でビルドすると、`jp` タグが有効になる。
- `go build -tags en main.go` でビルドすると、`en` タグが有効になる。

#### 実行

- ビルドしたファイルは`./main` で実行する。
- `go run -tags jp main.go` で実行すると、`jp` タグが有効になる。
- `go run -tags en main.go` で実行すると、`en` タグが有効になる。

#### settings.json の設定

以下を追加しないと、静的解析がうまくいかない。

```json
 "go.toolsEnvVars": {
    "GOFLAGS": ["-tags=en", "-tags=jp"]
  },
```

参考: https://github.com/golang/go/issues/29202
