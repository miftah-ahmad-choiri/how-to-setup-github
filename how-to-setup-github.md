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
$
```