# work-flow

Don't panic!

## 普通 PR 流程

1. fork 本项目
2. 用户 A 从 master checkout 一个新的分支，名叫 new\_doc，然后添加一个文件 a.md ，提交到 A 的仓库中
3. 用户 A 提交 PR 到 Nethell/work-flow 的 master 分支
4. 用户 B 与用户 A 对 PR 进行 review，通过后合并 PR
5. 用户 B 在本地添加 remote 追踪 Nethell/work-flow: `git remote add upstream git@github.com:Nethell/work-flow`
6. 用户 B 在本地的 master 分支 `pull upstream 的 master 分支: git fetch upstream && git pull upstream master`
7. 用户 B 将 upstream 的更新同步到自己的远端仓库: `git push origin master`
8. 用户 B 从 master checkout 一个新的分支，名叫 update\_doc，修改 a.md 这个文件，然后提交到 B 的仓库中
9. 用户 B 提交 PR 到 Nethell/work-flow 的 master 分支
10. 用户 A 与用户 B 对 PR 进行 review，通过后合并 PR

## 同时存在多个 PR 时的流程

### bad 

1. 用户 A 与 upstream 同步: `git checkout master && git pull upstream master && git push origin master`
2. 用户 A 从 master 新建分支: `git checkout -b modify_doc`
3. 用户 A 修改 a.md ，将 ‘Hello world' 修改为 'hello user A'
4. 用户 A 将修改提交: `git commit -m 'modify a.md' && git push origin modify_doc`
5. 用户 A 提交 PR

-----

6. 用户 B 与 upstream 同步: `git checkout master && git pull upstream master && git push origin master`
7. 用户 B 从 master 新建分支: `git checkout -b modify_doc`
8. 用户 B 修改 a.md ，在文件尾部新建一行，内容为 'hello world'
9. 用户 B 将修改提交: `git commit -m 'modify a.md' && git push origin modify_doc`
10. 用户 B 提交 PR

-----

11. 用户 A 与 B review 用户 A 的 PR，通过后合并
12. 用户 A 删除分支 modify\_doc: `git push origin :modify_doc`
12. 用户 A 与 B review 用户 B 的 PR，通过后合并
13. 用户 B 删除分支 modify\_doc: `git push origin :modify_doc`

-----

13. 查看提交历史图: [network](https://github.com/Nethell/work-flow/network)

### good

1. 用户 A 与 upstream 同步: `git checkout master && git pull upstream master && git push origin master`
2. 用户 A 从 master 新建分支: `git checkout -b modify_doc`
3. 用户 A 修改 a.md ，将 ‘Hello world' 修改为 'hello user B'
4. 用户 A 将修改提交: `git commit -m 'modify a.md' && git push origin modify_doc`
5. 用户 A 提交 PR

-----

6. 用户 B 与 upstream 同步: `git checkout master && git pull upstream master && git push origin master`
7. 用户 B 从 master 新建分支: `git checkout -b modify_doc`
8. 用户 B 修改 a.md ，将 'hello world' 修改为 'hello user A'
9. 用户 B 将修改提交: `git commit -m 'modify a.md' && git push origin modify_doc`
10. 用户 B 提交 PR

-----

11. 用户 A 与 B review 用户 A 的 PR，通过后合并
12. 用户 A 删除分支 modify\_doc: `git push origin :modify_doc`
13. 用户 B 同步 upstream: `git checkout master && git pull upstream master && git push origin master`
14. 用户 B 进行 rebase: `git checkout modify_doc && git rebase master && git push origin modify_doc -f`
15. 用户 A 与 B review 用户 B 的 PR，通过后合并
16. 用户 B 删除分支 modify\_doc: `git push origin :modify_doc`

-----
17. 查看提交历史图: [network](https://github.com/Nethell/work-flow/network)
