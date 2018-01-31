# 分支（Branch）

## 切換分支

```shell
git checkout branch_name
```

## 切換到指定 commit

```shell
git checkout bc29f91
```

## 查詢目前所在位置 hash

```shell
git rev-parse HEAD
```

```shell
git rev-parse --verify HEAD
```

## 查詢 hash 對應名稱

```shell
git show-ref
```

```shell
git for-each-ref
```