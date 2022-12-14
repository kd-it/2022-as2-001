# 問題1

ポッド `ex1` を作成して、クラスタ上でコマンドを実行させてみましょう。

- 起動するイメージは `alpine`
- コンテナ内で実行するコマンドは `hostname`

コマンド `hostname` の効果により、ポッドのホスト名が出力されることになるため、正しく起動できた場合はポッド名がそのまま出力される。

```
PS> kubectl apply -f ex1
# 少し待つ(get podsでcompletedと出れば完了しています)
PS> kubectl logs ex1
ex1
```

ファイル `ex1.yml` にある程度のコードを入れて用意しているので、適宜書き換えて適用、チェックしてからコミットすること。

# 注意

この場合はポッド名がそのままホスト名として出力されるので、ポッド名を`ex1`から任意名に変更した場合、それに追随するはずです。
評価ではこの部分もテストします(単純にex1を吐き出すようなコードはNGということです)。
