# Git 版本控制

## cmd 基本操作

| 指令 | 註釋 | 備註 |
| -------- | -------- | -------- |
| pwd    | 取得目前所在的位置     | Text     |
| ls      | 查看所有目錄     | Text     |
| ls -I     | Text     | Text     |
| ls -Ih     | Text     | h(human)     |
| cd     | Text     | Text     |
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

| Column 1 | Column 2 | Column 3 |
| -------- | -------- | -------- |
| git diff     | 比較修改前後的檔案內容     | Text     |
| git show     | 顯示commit修改紀錄<br>`git show master後面版本號`<br>`git log --oneline` | 接ID    |
| gitk     | Text     | ![](https://i.imgur.com/VKepjWV.png)|
|      |      | Text     |
|       | Text     | Text     |
| Text     | Text     | Text     |
| Text     | Text     | Text     |


#### 取得remote資訊
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

#### 共同pull push clone同一個repository
記得要將repository collaborators給共用人員
![](https://i.imgur.com/iEyrrZI.png)


## 上課文件
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