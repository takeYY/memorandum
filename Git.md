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
* branch_name
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
$ git reset --hard HEAD
```
- マージ後、既にコミットした場合
```shell=
$ git reset --hard ORIG_HEAD
```

## pull
リモートの変更をローカルにも反映
```shell=
$ git pull
```

## rebase
fast-forward（変更履歴を一本化）  
**rebase前**  
1-2ー3-4-5-6-master  
　　l-7-8-9-branch_name  
===>  
**rebase後**  
master-7-8-9-branch_name  

1. rebaseしたいブランチに移動しrebase
    ```shell=
    $ git checkout branch_name
    $ git rebase master
    ```
2. Conflict（競合）したファイルを手動で変更
3. 全て完了したら、addで追加してcontinue
    ```shell=
    $ git add <Conflictした/path/to/ファイル名>
    $ git rebase --continue
    ```
4. 再びConflict（競合）が起こったら2.に戻る
5. 全てのrebaseが完了したら、以下でpull
    ```shell=
    $ git pull
    ```
6. 最後に、いつものリモートにpush
    ```shell=
    $ git add .
    $ git commit
    $ git push
    ```

## tag
tag付けることで、バージョン指定した状態をzipダウンロード可能となる
```shell=
$ git tag 1.0
$ git push --tag origin master

Total 0 (delta 0), reused 0 (delta 0)
To git@github.com:{GitHubアカウント名}/{プロジェクト名}.git
* [new tag]         1.0 -> 1.0
```

###### tags: `development`,`開発`,`git`
