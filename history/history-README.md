# 歷史

## 顯示目前圖形化 commit Log 紀錄

```shell
# 圖形化紀錄
git log --oneline --graph
```

![git log --oneline --graph](./images/git-log-oneline-graph.png)

```shell
# 包含時間資訊
git log --oneline --graph --pretty=format:"%h <%an> %ar %s"
```

![git log --oneline --graph](./images/git-log-oneline-graph-pretty-format.png)

```shell
# 找到指定作者 KeJyun 的 Log 紀錄
git log --oneline --graph --author="KeJyun"
```

![git log --oneline --graph](./images/git-log-oneline-graph-author.png)

```shell
# 找到指定作者 KeJyun 或 KJ 的 Log 紀錄
git log --oneline --graph --author="KeJyun\|KJ"
```

![git log --oneline --graph](./images/git-log-oneline-graph-multi-author.png)

```shell
git log --oneline --graph --decorate --all
```

![git log --oneline --graph](./images/git-log-oneline-graph-decorate-all.png)


```shell
git log --pretty=oneline --graph --decorate --all
```

![git log --oneline --graph](./images/git-log-oneline-graph-decorate-all-pretty.png)

```shell
git log --oneline --graph --color --all --decorate
```


## 搜尋指定 commit 訊息的 Log 紀錄

```shell
git log --oneline --grep="文章"
```

## 顯示樹狀 log

```shell
git log --graph --oneline --all
```

```shell
git log --graph --pretty=oneline --abbrev-commit
```

```
$ git log --graph --pretty=oneline --abbrev-commit
*   74eff4f Merge branch 'feature/jwt_auth_package_update' of github.com:kejyun/kejyun
|\
| * 6ad01dd [jwt] upgrade jwt package at frontend
| * 7690a01 [package] - jwt upgrade
* | 8b25aeb [test] - codedeploy
* | d172c17 [test] - code deploy
* | 37474c1 [Module] - add KJModule
* | 1c6c4c5 [test] - test code deploy
|/
* 1150a44 [modify] - job update
```

## 參考資料
* [gitk - Viewing full version tree in git - Stack Overflow](https://stackoverflow.com/questions/5361019/viewing-full-version-tree-in-git)
* [Unable to show a Git tree in terminal - Stack Overflow](https://stackoverflow.com/questions/1064361/unable-to-show-a-git-tree-in-terminal)
