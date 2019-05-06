# tenma_research

開発環境には[Docker](https://www.docker.com/)を利用します

```
# イメージ作成(Dockerfileがあるディレクトリで実行)
$ docker build ./ -t tenma_research

# コンテナ作成
$ docker run -v $PWD:/work -itd -p=18000:80 --name tenma_research_01 tenma_research

# Docker内でpython実行
$ docker exec -ti tenma_research_01 python <hogehoge.py>

# コンテナをsshのように対話的に利用する
$ docker exec -ti tenma_research_01 bash

# コンテナの停止
$ docker stop tenma_research_01

# コンテナの開始
$ docker start tenma_research_01
```

モジュールを追加する際には、requirements.txtに記載してください
```
# ファイルを編集
$ vim requirements.txt

# コンテナを再ビルド（Dockerfileでpipを実行しています）
# 必要に応じて、イメージとコンテナを削除
$ docker rm -f tenma_research_01
$ docker build ./ -t tenma_research
$ docker run -v $PWD:/work -itd --name tenma_research_01 tenma
$ docker exec -ti tenma_research_01 pip list
```

