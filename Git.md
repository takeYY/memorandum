# Git
Gitを使ったバージョン管理

## 設定
```shell=
$ git config --global user.name "Your Name"
$ git config --global user.email your.email@example.com
```

## セットアップ
```shell=
$ git init
```

## 状態確認
```shell=
$ git status
```

## コミット
```shell=
$ git commit -am "Commit name"
```
`-a`:ワークツリーで変更済みのファイルをコミットする（「git add」コマンドによる操作を省略
ただし、初回のみ管理対象を決めるために`git add`コマンド操作が必要  
`-m`：""内の文字列をメッセージとして設定可能

## プッシュ
```shell=
$ git push
```

## ログ
```shell=
$ git log
```
ログがある程度以上長い場合は、qキーを押して終了

## ブランチ
- ブランチ作成
```shell=
$ git checkout -b branch_name
```
`-b`:新しいブランチ作成
- ブランチ一覧
```shell=
$ git branch
master
* branch-name
```
「*」は現在使用中のブランチ
- ブランチ移動
```shell=
$ git checkout branch_name
```

## ローカルのブランチをリモートにも追加
```shell=
$ git push --set-upstream origin branch_name
```
リモートに既にブランチが存在している場合は必要ないはず

## マージ
```shell=
$ git checkout master
Switched to branch 'master'

$ git merge branch_name
```
branchNameをmasterにマージ

## マージの取り消し
- マージ後、まだコミットしていない場合
```shell=
git reset --hard HEAD
```
- マージ後、既にコミットした場合
```shell=
git reset --hard ORIG_HEAD
```


###### tags: `development`,`開発`,`git`
