# git使用场景

## 代码下载

### fork项目

   - `git clone git@github.com:wnlm/pili-rtc-wxapp.git`
   - `git remote add upstream git@github.com:qbox/pili-rtc-wxapp.git`
   - `git checkout -b dev`

### 更新和提交代码

   - 更新代码
   - `git pull upstream master`
   - 提交本地修改
   - `git add `
   - `git commit -m "..."`ud
   - `git push origin dev`

### 提交pr

## Github进行fork后，如何与原仓库同步

- `git fetch upstream`   抓取公司仓库的更新
   - `git checkout master`  切换到 master分支
   - `git merge upstream/master`  合并远程的master分支
   - `git push origin master`  把本地仓库向github仓库(fork到自己名下的仓库)推送修改
   - `git log`  查看自己名下的仓库和公司仓库是否一致
   - 此时master分支已与公司仓库同步，若想制定 特定分支(如：dev)与master一致，执行下面命令
   - `git checkout dev`
   - `git merge master`

## bug分支

> **注意**：加入当前正在用 dev 分支工作，临时需要在 master 上建立一个 bug 分支。但是此时 dev 分支存在未提交的内容不能进行切换分支，Git提供一个`stash`功能，可以把工作现场存储起来。
   - `git stash`  将工作区内容暂时存储在某个地方
   - `git status`，此时工作区是干净的。此时可以切换分支
   - 当我们的bug分支问题处理完成之后，切回dev分支，
   - 使用 `git stash pop`  返回工作现场
> **注意**：dev分支是在 master 上建立的，这时dev分支上存在bug分支上的bug问题，git 提供 `cherry-pick` 命令，可以复制一个特定的提交到当前分支。
   - git cherry-pick bug分支commit的特殊值

## 版本回退

   - 查看从近到远的提交日志
   - `git log`
    commit 2aa5ac52f6e9079a15913da8f5292c60daf256c2 (HEAD -> master, upstream/master, origin/master, origin/HEAD, dev, QRTC-515)
	Merge: 07d50a4 8853c30
	Author: KevinHuo <kevinhuox@gmail.com>
	Date:   Tue Sep 22 19:03:28 2020 +0800

    	Merge pull request #26 from wnlm/QRTC-515

    	[QRTC-504] update version

	commit 8853c3054a8b62a1b99330acda3dbc73cf4999e0 (origin/QRTC-515)
	Author: wnlm <2416074279@qq.com>
	Date:   Tue Sep 22 18:12:35 2020 +0800

    	update version QRTC-515

	commit 5b9c55977b60854a527ff0791e6680c09a4124d5
	Author: wnlm <2416074279@qq.com>
	Date:   Tue Sep 22 17:19:55 2020 +0800

    	update version
   - HEAD 表示当前版本，HEAD^表示上一版本，HEAD表示^^表示上上一个版本。
   - 回退上一版本
   - git reset --hrad HEAD^   此时，已回退上一版本。就好像从21世纪回退到20世纪。
>**注意**：此时，我们后悔了，想要找回未来的版本。如果找不到未来版本的 commit id ，git 提供了一个命令 `git reflog` 记录每一次的命令，以便确定要回到未来的哪个版本。
   - `git reset --hard 想要指定的未来版本号（commit id）`

## git之追加提交与合并提交

https://www.jianshu.com/p/6c7fea49172b




