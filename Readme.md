# Git 版本控制


## cmd 基本操作

| 指令 | 註釋 | 備註 |
| -------- | -------- | -------- |
| pwd    | 取得目前所在的位置     | Text     |
| ls      | 查看所有目錄     | Text     |
| ls -I     | Text     | Text     |
| ls -Ih     | Text     | h(human)     |
| cd     | 開啟     | Text     |
| Man  (可接l, ls…)<br>Command-name --help(win)| 使用手冊     | 像是ls可以搭配-l查看詳細資料     |
| clear     | Text     | Text     |
| touch     | 建立檔案     | Text     |
| mkdir     | 建立目錄     | Text     |
| rm     | 刪除檔案     | Text     |
| cp     | 複製     | cp 複製的檔案 新檔案名稱     |
| cp -r     | 複製目錄     | Text     |
| rm     | 移除檔案     | Text     |
| rm -rf     | 刪除目錄     | Text     |
| mv     | 移動檔案/修改名稱     | mv 要搬的 般到哪     |
| cat     | 看檔案內容     | Text     |



## git 基本操作

| 指令 | 註釋 | 備註 |
| -------- | -------- | -------- |
| git diff | 比較修改前後的檔案內容     | ![](https://i.imgur.com/2vqyBDv.png) |
|git diff --cached|顯示暫存區的diff(add後尚未commit的diff||
|git diff --name-status(--cached)|顯示在工作目錄上的所有檔案狀態(暫存區)||
| git show     | 顯示commit修改紀錄<br>`git show master後面版本號`<br>`git log --oneline` | 接ID![](https://i.imgur.com/2HSxSTB.png)|
| gitk     | Text     | ![](https://i.imgur.com/VKepjWV.png)|
|git reset --hard|      | Text     |
|git cherry-pick <shal>|merge其中一個commit     | 常用     |
| git reflog     | 看所有HEAD的commit紀錄     | Text     |
| git rebase <sha1>    | 不會有分支的合併(會重寫commit)  | 出現太多問題建議<br>git rebase --abort   |

![](https://i.imgur.com/LQKOuJm.png)

    
### Log紀錄
```c++
# 搜尋有關keyword的紀錄(有分大小寫)
git log -S <keyword>
  
# 使用限定日期搜尋
git log --since --until
git log --since=2019-7-31

# 限定使用者
git log --author
git log --author=Nick
git log --author=rich0432
git log --author=rich0432@gmail.com
    
# 只顯示最新的n筆commit
git log -n <number>

# 顯示樹狀結構
git log --all --decorate --oneline --graph --color=always
    
```
 

    
### checkout查看功能
```c++
# 移動到shal的commit
git checkout <sha1>    

# 移動到head的commit
git checkout HEAD      

# 將shal中file的檔案紀錄放置進head
git checkout <sha1><file>    

#取出shal的所有檔案至工作目錄
git checkout <shal> .    

# 在HEAD新建分支同時前往所新建的分支
git checkout -b <branchname>
```
**取消更改的內容(在git add之前)**
```c++
#回到HEAD的內容
git checkout HEAD <file>
也等同於
git checkout -- <file>

#還原所有修改過的資料
git checkout -- .
```
    
### Remote取得資訊
```c++
git remote show origin
```
![](https://i.imgur.com/ah1RhdH.png)

```c++
git remote -v 
# git remote add origin https://XXXX
```
:::info
**`origin`** 為遠端倉庫名稱 是可更替
:::
    
### Branch增加新分支
把commit加名字
```c++
# 在目前的HEAD建立分支
git branch <branchname> 

# 在目前HEAD上幫其他commit建立分支
git branch <bn> <shal>

# 刪除分支(可刪除多個)
git branch -D <branchname>
    
# 列出所有的分支名稱
# (-av：名稱+內容 -a：只顯示分支名稱)
git branch -av
git branch -a
    
# 設定遠端分支
git push --set-upstream-to=origin/<bn> <bn>
ex:
git push --set-upstream bn-1 #bn-1的local跟遠端會連起來

# 將HEAD的資料update進origin的branchname
git push origin <branchname>
    
# 刪除遠端分支
git push origin :<bn>

# 刪除已經沒有遠端分支的遠端追蹤分支
git remote prune origin
 ps.在遠端介面刪除branch後，與本機紀錄同步。
```

### Merge合併分支

```C++
# 合併兩個分支(把<branchname>合併到HEAD)
git merge <branchname>

#取消merge
git merge --abort
```

### git merge vs git rebase
**merge**：兩個分支合併時產生新的commit    
**rebase**：兩個分支合併時重寫comm it，通常用在美化git圖(一直線) 
    
### Reset
![](https://i.imgur.com/Zhg7MxF.png)

### Revert還原功能
與reset的差別為 Revert會多出commit紀錄
    
### Stash已修改的檔案放一邊
![](https://i.imgur.com/8x6uSxS.png)


    


    


### 解決衝突(當遇到兩個commit同時修改同一份file)

1. <font color=red>`git merge <branchname or shal>`</font>
2. 若看到衝突訊息
3. code開啟文件解決衝突
4. <font color=red>`git add .`</font>
5. <font color=red>`git commit`</font>



:::warning
進入vim介面時為何要一直按Esc
:::


### 共同pull push clone同一個repository
記得要將repository collaborators給共用人員
![](https://i.imgur.com/iEyrrZI.png)

### bisect二分搜尋法
```C++
# 開始二分搜尋法
git bisect start
git bisect good/bad

# 結束二分搜尋法
git bisect reset
```
    
    
    
    
    

    
## 上課文件
    
    
    
### 三種存取模型
**分散式貢獻者模型(dispersed)**
![](https://i.imgur.com/99eXOaJ.png)
**共處一地貢獻者模型(collocated)**
![](https://i.imgur.com/lgiD5Xx.png)
**共享維護模型(shared)**
![](https://i.imgur.com/29BWmzZ.png)

### 主線開發與搭配分支開發    
![](https://i.imgur.com/C4W46gE.png)
    
![](https://i.imgur.com/37iHXEo.png)

### 一功能一分支
![](https://i.imgur.com/ONr8i9R.png)
    
### Github flow
![](https://i.imgur.com/IRcld1b.png)

### GitLab flow & Gitworkflows
![](https://i.imgur.com/DONwmpm.png)

* **featureA**：功能A
* **featureB**：功能B
* **develop**：開發測試區
* **staging**：測試階段區
* **master**：主線

![](https://i.imgur.com/Omq7TVx.png)
* **maint**：maintain也是主線
* **next**：下個階段區
* **pu**：propose update提出更新的功能

![](https://i.imgur.com/cut9Q6y.png)
   
### Gitflow
![](https://i.imgur.com/HurC6wL.png)
![](https://i.imgur.com/YjSeO1D.png)
    
![](https://i.imgur.com/48iAPP5.png)


### gitignore
建立後可紀錄不想push的檔案<br>
之後<font color=red> `git add .` </font>之時變不會出現在工作目錄上


### GitLab(專案可視度)
![](https://i.imgur.com/ScwXryd.png)
![](https://i.imgur.com/7byQo2M.png)

    
### GitLab(權限等級)
![](https://i.imgur.com/O4cddQs.png)

    
### GitLab(受保護的分支)
![](https://i.imgur.com/iMQ7uEX.png)


## 補充文件
因為這個單元之後都會使用 git-tree 這個指令，所以要安裝 git-tree 這個指令，以下是安裝方式

### 先安裝 tmux (Windows)
- 下載 https://drive.google.com/open?id=15YIS3aZ5OEmAlNSOCwucRNo3_ZGRDFIP
- 將 git-tree-lib-64.zip 裡面的三個檔案解壓縮到 C:\Program Files\Git\usr\bin

### 先安裝 tmux (Mac/Linux)
- 安裝方式：https://larrylu.blog/tmux-33a24e595fbc
- 注意：文內 Mac 的 Homebrew 安裝方式已經失效，可以用下面這個指令喔

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### 再安裝 git-tree (Windows/Mac/Linux)
git-tree 安裝說明：https://gist.github.com/kewang/8c478078f2a98f32f5bcbfca1348a8a1#file-readme-md

## 參考文件
https://hackmd.io/aEnSQltrQ2ad1P2sjT_jAw?both


## 超好用功能
### Terminal Open VS code
[安裝說明文件](https://www.ucamc.com/articles/423-%E5%A6%82%E4%BD%95%E5%BE%9Emacos%E4%B8%8A%E7%9A%84%E7%B5%82%E7%AB%AF%E6%A9%9Fterminal%E6%89%93%E9%96%8Bvisual-studio-code%EF%BC%9F)

指令：
```python
code   #要開的資料夾
code . #開啟整個資料夾
```


### 程式冷知識
[**Github**中master改為main的原因！！](https://technews.tw/2020/09/22/github-to-replace-master-with-main-starting-next-month/)