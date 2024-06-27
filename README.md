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

#### 実行結果

ビルドタグによって、出力される文字列が変わる。

- `jp` タグが有効な場合
  - `こんにちは`
- `en` タグが有効な場合
  - `Hello`

#### settings.json の設定

以下を追加しないと、静的解析がうまくいかない。ただし、SayHello() 関数名の重複はエラーが出る。

```json
 "go.toolsEnvVars": {
    "GOFLAGS": ["-tags=jp,en"]
  },
```

参考: https://github.com/golang/go/issues/29202
