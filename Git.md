====Git Skills====
--Sunic Yosen
--Oct 28 2018
--Learn from: https:##www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000

0.Git Environment
  0) Install Git: sudo apt install git
  1) Set user: git config --global user.name "Your Name"
               git config --global user.email "email@example.com"

1.Git usage
  git init             ##Init repository

  git add <filename>   ##Add file to git repository 
    ##[把文件添加进去，实际上就是把文件修改添加到[暂存区]]
  
  git commit -m <meaasage> ##Commit of this update and give comment with <-m> [提交&注释]
    ##[提交更改，实际上就是把暂存区的所有内容提交到当前分支]

  git status           ##The status of repository
    
  git diff  <filename> ##The changes detail of file
    <repository>       ##Give the Version id
    HEAD               ##Current version
    eg: git diff HEAD -- <filename>
        git diff --cached 
        [比较的是暂存区的文件与仓库分支里（上次git commit 后的内容）的区别。] 

  git log              ##List the log/Journal of repository
    --pretty=oneline   ##List one line of a log

  git reset            ##return to last version
    --hard
      HEAD        ##Cuurent version
      HEAD^       ##Last version
      HEAD^^      ##Last second version
      HEAD~100    ##Last 100th version
      eg: git reset --hard HEAD^   ##Return last version
      <commit id> ##Return/Forward to <commit id> version
                  ##Could Just Give the front of commit id

  git reflog      ##Record all command, so you can call back.[会退到任意位置]

  git checkout -- <filename>  ##Callback last version when not add modify to Repository
    ## -- is important. 
    ##[尚未添加到暂存区，手动把文件恢复到上一个版本的状态，如果已经添加到Stage，那么回退到添加之后]
    ##['git checkout -- '其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”]
    ##If have added to stage, 'git reset HEAD <file>' could callback, and then 'git checkout --'
    ##If you have committed, 'git reset --hard <commit id> to return last version.
  
  git rm <filename>
    ##Remove file from repository. Then you should 'git commit -m <meaasage>' to commit to repository

  git remote add origin <remote Address>
    ##Add remote repository named <origin> 
    ##[关联一个远程库]
    
  git push ##Push to remote
    -u ##Used at the first time. 
       ##Git will push local repository to remote, 
       ##And it will make connect between local and remote.
    origin ##Remote repository name.
    master ##Remote branch name.
    eg: git push -u origin master [First time]
        git push origin master
    
  git check ##Branch usage
    -b  ##Create 
  


2.Git branch


3.Git knowledge
   a) .git
     .git folder is the version repository.[版本库]
       Stage/index [暂存区] [需要提交的文件修改通通放到暂存区，然后一次性提交暂存区的所有修改]
       branch [分支] -> First branch: master -> pointer: HEAD
       |-----------|            |----------------------------------|
       | WorkSpace |            |             Repository           |
       |           |            |                                  |
       |   |File1  |            |  |----------|  HEAD->|--------|  |
       |   |File2  |   Git Add  |  |  Stage   |        | Master |  | 
       |   |Folder |----------->|  |   File1  | Commit |  File1 |  |
       |     |Fl1  |            |  |   File2  |------->|  File2 |  |
       |     |Fl2  |            |  |          |        |   ...  |  |
       |           |            |  |----------|        |--------|  |
       |-----------|            |----------------------------------|

   b) Status for working tree.
       Changes not staged for commit  ##Have not staged
       Changes to be committed        ##Have not committed
       nothing to commit, working tree clean ##Clean


