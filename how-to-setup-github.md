# How to setup github for myPC

```{ .git .copy title="mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING"}
mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ cat ~/.bash_profile
export MY_PATH="/c/Users/mifta/OneDrive - IBM/IBM/LEARNING"
alias mydir='cd "$MY_PATH"

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ git --version
git version 2.47.1.windows.1

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ git config --global user.name "miftah-ahmad-choiri"

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ git config --global user.email "miftahcoiri354@gmail.com"

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/etc/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.name=miftah-ahmad-choiri
user.email=miftahcoiri354@gmail.com

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ ssh-keygen -t ed25519 -C "miftahcoiri354@gmail.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/mifta/.ssh/id_ed25519): 
Enter passphrase for "/c/Users/mifta/.ssh/id_ed25519" (empty for no passphrase):
Enter same passphrase again: 
Your identification has been saved in /c/Users/mifta/.ssh/id_ed25519
Your public key has been saved in /c/Users/mifta/.ssh/id_ed25519.pub    
The key fingerprint is:
SHA256:Ykz9mrMUfVzGft+KrmnDWGFfu/ra6xDY3lEahjR3Cm0 miftahcoiri354@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|            +.. .|
|       .   . *Eo |
|      . .   ..B .|
|     o   oo+ =.+ |
|      + S.+o=.+..|
|     . . +.o.o.oo|
|        =+  o ..o|
|       ..o+. +.. |
|        ..o+==*. |
+----[SHA256]-----+

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ eval "$(ssh-agent -s)"
Agent pid 648

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ ssh-add ~/.ssh/id_ed25519
Identity added: /c/Users/mifta/.ssh/id_ed25519 (miftahcoiri354@gmail.com)

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ cat ~/.ssh/id_ed25519.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIMu6xKmYHzgM+cXqrrr7UsUJBje2bJluJNzthtMGWxRw miftahcoiri354@gmail.com

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ ssh -T git@github.com
The authenticity of host 'github.com (20.205.243.166)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
git@github.com: Permission denied (publickey).

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ ssh -T git@github.com
Hi miftah-ahmad-choiri! You've successfully authenticated, but GitHub does not provide shell access.

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ cd github/how-to-setup-github/

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git init

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github/how-to-setup-github (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)   
        how-to-setup-github.md

nothing added to commit but untracked files present (use "git add" to track)

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git add how-to-setup-github.md 

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git commit -m "second commit"
[main 9ec9931] second commit
 1 file changed, 88 insertions(+)
 create mode 100644 how-to-setup-github.md

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git status
On branch main
nothing to commit, working tree clean

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git remote add origin git@github.com:miftah-ahmad-choiri/how-to-setup-github.git
error: remote origin already exists.

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git push -u origin main
ERROR: Repository not found.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ gh --version
bash: gh: command not found

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ "/c/Program Files/GitHub CLI/gh.exe" --version
gh version 2.66.1 (2025-01-31)
https://github.com/cli/cli/releases/tag/v2.66.1

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ vi ~/.bash_profile

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ gh --version
bash: gh: command not found

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ source ~/.bash_profile

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ gh --version
gh version 2.66.1 (2025-01-31)
https://github.com/cli/cli/releases/tag/v2.66.1

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ cat ~/.bash_profile
export MY_PATH="/c/Users/mifta/OneDrive - IBM/IBM/LEARNING"
alias mydir='cd "$MY_PATH"'
export PATH=$PATH:/c/Program\ Files/GitHub\ CLI

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ gh repo view --web
To get started with GitHub CLI, please run:  gh auth login
Alternatively, populate the GH_TOKEN environment variable with a GitHub API authentication token.

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ gh auth login
? Where do you use GitHub? GitHub.com
? What is your preferred protocol for Git operations on this host? SSH
? Upload your SSH public key to your GitHub account? C:\Users\mifta\.ssh\id_ed25519.pub
? Title for your SSH key: (GitHub CLI)

? Title for your SSH key: GitHub CLI
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: A914-4CC7
Press Enter to open https://github.com/login/device in your browser...
✓ Authentication complete.
- gh config set -h github.com git_protocol ssh
✓ Configured git protocol
✓ SSH key already existed on your GitHub account: C:\Users\mifta\.ssh\id_ed25519.pub
✓ Logged in as miftah-ahmad-choiri

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING
$ gh repo view --web
failed to run git: fatal: not a git repository (or any of the parent directories): .git

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ gh repo view --web
GraphQL: Could not resolve to a Repository with the name 'miftah-ahmad-choiri/how-to-setup-github'. (repository)

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ gh repo list

Showing 3 of 3 repositories in @miftah-ahmad-choiri

NAME                                     DESCRIPTION                              INFO     UPDATED                                                                                                                                                    
miftah-ahmad-choiri/skills-github-pages  My clone repository for github pages     public   about 2 hours ago
miftah-ahmad-choiri/skills-introduct...  My clone repository                      private  about 15 hours ago
miftah-ahmad-choiri/miftah-ahmad-choiri  My personal repository to introducin...  public   about 16 hours ago


mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ gh repo create how-to-setup-github --public --source=. --remote=origin --push
✓ Created repository miftah-ahmad-choiri/how-to-setup-github on GitHub
  https://github.com/miftah-ahmad-choiri/how-to-setup-github
X Unable to add remote "origin"

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git remote -v
origin  git@github.com:miftah-ahmad-choiri/how-to-setup-github.git (fetch)
origin  git@github.com:miftah-ahmad-choiri/how-to-setup-github.git (push)

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git remote remove origin

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git remote -v

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git remote add origin git@github.com:miftah-ahmad-choiri/how-to-setup-github.git

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ git push -u origin main
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 1.72 KiB | 1.72 MiB/s, done.
Total 6 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:miftah-ahmad-choiri/how-to-setup-github.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

mifta@Miftah-PC MINGW64 ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github (main)
$ gh repo list

Showing 4 of 4 repositories in @miftah-ahmad-choiri

NAME                                     DESCRIPTION                              INFO     UPDATED           
miftah-ahmad-choiri/how-to-setup-github                                           public   about 1 minute ago
miftah-ahmad-choiri/skills-github-pages  My clone repository for github pages     public   about 2 hours ago 
miftah-ahmad-choiri/skills-introduct...  My clone repository                      private  about 15 hours ago
miftah-ahmad-choiri/miftah-ahmad-choiri  My personal repository to introducin...  public   about 16 hours ago
```