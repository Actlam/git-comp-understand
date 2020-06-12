# git-comp-understand
git完全理解者(強気)になるためのリポジトリ

| commit | 扱ったファイル | やったこと                                                   |
| ------ | -------------- | ------------------------------------------------------------ |
| 1      | index.js       | 一番初めのcommit                                             |
| 2      | second.html    | ２番目のコミット                                             |
| 3      | Third.py       | devブランチを切ってプルリクを投げて承認するまでを試した<br />(https://qiita.com/takamii228/items/80c0996a0b5fa39337bd) |
| 4      |                | feature/devブランチも同様にmasterの変更に追従させた<br />(該当ブランチでgit merge origin masterの後push) |
| 5      |                | rebaseでリポジトリの更新を試み(途中)                         |
|        |                |                                                              |
|        |                |                                                              |
|        |                |                                                              |
|        |                |                                                              |



## コマンドメモ

### (3)ブランチの作成

- Branch-nameにはチケット番号や開発機能名をつけることが多い

```shell
git checkout -b feature/{branch-name}
```

### (3)間違えてaddしてしまったときにaddを取り消したい

```shell
git reset
# 特定のファイルだけ取り消したい
git reset <特定のファイル>
```

### (3)コミットメッセージを書きたい

```shell
git commit -m "コミットメッセージ"
```

### (3)直前のcommitを修正したい

```shell
git commit --amend
```

### (3)レポジトリの状態確認

 とりあえずこれ

```shell
git status
```

### (3)ローカルからリモートへプッシュするとき、リモートが更新されていればローカルに変更を取り込む

git pull(fetch + merge)は慣れるまで使わないほうがよさそう

featureブランチ切ってたりするとrebase使ってリモートのmaster→ローカルのfeatureに反映させたりする必要がある

```shell
# リモートの更新をローカルに取り込む
git fetch

# 現在のブランチにmasterの変更を取り込む
git merge origin master

# 競合を解消する
git add example.md
git commit

# pushするよ
git push origin feature/xxx

```

実はrebase使っても似たようなことができるよ

```sh
# 更新取り込み
git fetch

# 現在のブランチにmasterの更新を取り込む
git rebase origin master

# 競合起きたら解消
git add example.md
git rebase --continue

# pushするよ
git push origin feature/xxx
```



