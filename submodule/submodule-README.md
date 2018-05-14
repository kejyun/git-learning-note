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