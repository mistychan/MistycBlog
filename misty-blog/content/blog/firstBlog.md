+++
title = 'FirstBlog'
date = 2023-11-15T15:07:55+08:00
draft = false
+++
## 这是第一个blog文章
- hello world
- This is a front-end coder
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
git tag -d 1.2.5
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