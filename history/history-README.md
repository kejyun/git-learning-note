# 歷史

## 顯示目前圖形化 commit Log 紀錄

```shell
# 圖形化紀錄
git log --oneline --graph
# 包含時間資訊
git log --oneline --graph --pretty=format:"%h <%an> %ar %s"
# 找到指定作者 KeJyun 的 Log 紀錄
git log --oneline --graph --author="KeJyun"
# 找到指定作者 KeJyun 或 KJ 的 Log 紀錄
git log --oneline --graph --author="KeJyun\|KJ"
```

## 搜尋指定 commit 訊息的 Log 紀錄

```shell
git log --oneline --grep="文章"
```