# 子模組

## 加入子模組

***1.建立子模組 repository***

例如在 github 建立一個 KJModule 的子模組，建立完後一定要做一次 commit，這樣才可以順利的將子模組加入進去到其他專案

```
git@github.com:kejyun/KJModule.git
```


***2.加入子模組***

```
git submodule add <repository> [<path>]
```

```
git submodule add git@github.com:kejyun/KJModule.git ./app/KJModule
```

指定需要加入的子模組 Repository 以及子模組需要放到專案的哪個路徑中

## 抓取含有子模組的專案

***1.取得資源庫***

```
git clone git@github.com:kejyun/KJ.git
```

***2.初始化子模組並更新***

```
git submodule init
git submodule update
```

## 變更子模組 repository 路徑

在 git 子目錄有 `.gitmodules` 檔案，如果模組路徑要刪除或變更，需要修改此檔案

```
[submodule "app/KeJyunModule"]
	path = app/KeJyunModule
	url = git@github.com:kejyun/KeJyunModule.git
[submodule "app/KeJyunGroupModule"]
	path = app/KeJyunGroupModule
	url = git@github.com:kejyun/KeJyunGroupModule.git
```

在隱藏目錄 `.git` 中，找到你要變更的模組目錄的設定檔案

> .git/modules/<模組路徑>/config

```shell
vim ~/KeJyunProject/.git/modules/app/KeJyunModule/config
```

在 config 設定檔變更 `[remote"origin"]` 的 `url` 去變更子模組的路徑

```
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
	worktree = ../../../../app/KeJyunModule
[remote "origin"]
	url = git@github.com:kejyun/KeJyunModule.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
```
