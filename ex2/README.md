# 問題2

空のファイル`ex2.yml`を用意している。
このファイルを用いてポッド`echo`を作成せよ。

# ポッド`echo`の仕様

* ポッド名 echo
* ラベルとして `name`に対し`echo`を付与
* ポッド内のコンテナ名は任意(`echo`であってもなくてもよい)
* 利用するイメージは `k8s.gcr.io/echoserver:1.10` とする
    * イメージ名は手打ちでなくコピペ推奨
* リソース制限は初期値のままで良い
* コンテナが利用するポート(containerPort)として8080を宣言する

# テスト方法

このマニフェストを適用した場合、pod/echoが生成される。
ポートフォワードで露出させると、イメージの持つ「echo server」にアクセスできる。

```
PS> kubectl port-forward pod/echo 8080:8080
```

とすることで、ブラウザ等で http://127.0.0.1:8080/ にアクセスすると、サーバーとクライアントの情報を取得できる。

以下はブラウザの代わりに`curl`で取得した場合の例である。

```
PS> curl -s 127.0.0.1:8080

Hostname: echo

Pod Information:
	-no pod information available-

Server values:
	server_version=nginx: 1.13.3 - lua: 10008

Request Information:
	client_address=127.0.0.1
	method=GET
	real path=/
	query=
	request_version=1.1
	request_scheme=http
	request_uri=http://localhost:8080/

Request Headers:
	accept=*/*
	host=localhost:8080
	user-agent=curl/7.79.1

Request Body:
	-no body in request-
```

# 後始末を忘れないこと

* `kubectl port-forward` は止めておくこと
* 作ったポッドの削除も忘れずに
    * マニフェストを `kubectl delete` で渡す
    * `pod/echo` を同様に渡す

# おまけ

k8sでは別にDocker Hubでなくてもイメージのアドレスを指定すれば、(アクセスできるなら)そこから取得することができます。
この例では、K8sが公式にチュートリアル用に公開しているechoserverイメージを使っていますが、こちらはk8s.gcr.io(Google Container Registry)上のものを使っています。

