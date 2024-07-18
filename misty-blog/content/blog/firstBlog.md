+++
title = '开发笔记'
date = 2024-07-18T15:45:12+08:00
draft = false
+++

![这是一张图](https://gd-hbimg.huaban.com/4da7ca018b1813a5b28fa8ec95dd5f3999c02d3f336f24-ZOc5GU)
### 一、Git常用方法

#### 1.1 仓库推送方法

1. 将本地开发的记录在vscode的git管理工具中暂存

```js
git add .
```


2. 将修改的内容暂存后继续**存储暂存**，可以不设置暂存的名称，如有多个暂存可以设置

```js
git stash
```

3. 接下来就开始拉取远端的仓库代码，暂存代码就是为了避免本地和远端的代码不一致造成冲突

```js
git pull  //拉取远端仓库代码
```

4. 将暂存的代码弹出

```js
git stash pop
```

5. 弹出代码后，如果有冲突的地方，就根据情况选择传入的修改（暂存的）和原本的代码（仓库的），修改完成后保存代码

6. 暂存代码并本地提交，推送到仓库

```js
git add .
git commit -m '提交内容的描述文字'
git push
```

#### 1.2 git tag的用法

**git tag 作用**

tag是一个记录点，用于记录某个commit点或分支的历史快照，这样方便查找版本号，相比commit id 更加人性化，直接可以通过v1或v2查找对应发布版本的源码。

- 创建轻量标签

```js
git tag 1.2.3
```

-  注释创建的标签

```js
git tag -a 1.2.3 -m "标签的描述信息"
```

- 查看1.2.3版本的具体信息

```js
git show 1.2.3
```

- 将标签推送到远程

```js
git push origin 1.2.3
```

- 一次性推送多个标签到远程

```js
git push origin --tags
```

- 删除本地标签

```js
git tag -d 1.2.4
```

- 删除远程标签

```js
git push origin :refs/tags/1.2.3
```

#### 1.3 git撤销相关

- 撤销最近一次的commit操作

```js
git reset --soft HEAD^
```

#### 1.4 git merge 合并相关

- 先切换到需要合并到发分支（确保没有未提交的代码）

```js
git checkout dev
```

- 拉取该分支最新代码（一定确保pull成功）

```js
git pull
```

- 合并源分支

```js
git merge feat_20240603
```

- 处理合并过来的冲突代码

- 提交代码（commit + push）

#### 1.5 git合并代码

```js
git conifg pull.rebase false #merge
git conifg pull.rebase true #rebase
```

- **Merge（合并）**

  将两个分支的历史合并在一起，创建一个新的合并提交，保留了各自分支的提交历史。这会产生一个合并的提交节点，显示了两个分支的合并点。

- **Rebase（变基）**

  将当前分支的提交“移动”到另一个分支的最新提交之后，使得提交历史更加线性清晰。在变基过程中，会将当前分支的提交逐个应用到目标分支的最新提交上，不会产生合并提交。

总结：选择使用合并（Merge）的主要原因是合并是一种相对保守和安全的合并方式，不会改变提交历史，保留了分支的完整历史记录。此外，合并操作相对简单，易于理解和操作，适合大多数团队协作开发的需求。
