# AS2 課題1

今回は3つの課題を各ディレクトリに入れています。
3つのディレクトリそれぞれに`README`ファイルを置いていますので、中を見て対応してください。
ローカルのK8s環境(minikube環境)で適用、動作をチェックしてから提出してください。

動作しないYAMLを提出するとその部分の採点はできなくなります。

# 注意

各設問に用意された実行例などでは、minikubeを介さないかたちでkubectlを呼び出しています。

```
# 例
PS> kubectl get pods
```

minikubeを介して使っている場合は、実行時に適宜読み替えが必要なので、ローカル実行時は注意してください。

```
# 上記実行例を読み替えた例
PS> minikube kubectl -- get pods
```

なおこのルールは、今後の課題の中でも同様に適用されます。