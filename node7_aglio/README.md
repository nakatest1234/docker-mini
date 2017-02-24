# memo

* イメージ作成(ない場合)
```
$ docker build -t node7:aglio ./
```
* 実行
```
$ docker run -v ~/api-document:/mnt/api-document --rm -it node7:aglio /bin/bash cd /mnt/api-document; aglio -i sample.md -o sample.html
```
