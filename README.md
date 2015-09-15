# work-flow

Don't panic!

## 进度

1. fork 本项目
2. 用户 A 从 master checkout 一个新的分支，名叫 new_doc，然后添加一个文件 a.md ，提交到 A 的仓库中
3. 用户 A 提交 PR 到 Nethell/work-flow 的 master 分支
4. 用户 B 与用户 A 对 PR 进行 review，通过后合并 PR
5. 用户 B 在本地添加 remote 追踪 Nethell/work-flow: git remote add upstream git@github.com:Nethell/work-flow
6. 用户 B 在本地的 master 分支 pull upstream 的 master 分支: git fetch upstream && git pull upstream master
7. 用户 B 将 upstream 的更新同步到自己的远端仓库: git push origin master
8. 用户 B 从 master checkout 一个新的分支，名叫 update_doc，修改 a.md 这个文件，然后提交到 B 的仓库中
9. 用户 B 提交 PR 到 Nethell/work-flow 的 master 分支
10. 用户 A 与用户 B 对 PR 进行 review，通过后合并 PR
