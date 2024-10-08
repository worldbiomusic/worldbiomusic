---
title: "git 멀티계정"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Git]
tags: [git, 깃]
---

# 설명
깃헙 계정을 ssh와 git config를 이용해서 여러개 사용하는 방법이다

요약하면, 기존의 깃이 깃헙과 통신하는 과정은 HTTPS protocol 위에서 깃 사용자를 증명하는 방식이 깃헙에서 발행한 토큰을 깃에서 가지고 있는지 검사하는 것이었는데, 깃에서 토큰을 하나만 가지고 있을 수 있어서 다른 계정은 SSH protocol위에서 공개키 방식으로 검증해야 하는 것이다. 그래서 `ssh-keygen`으로 공개/비밀키를 만들고 공개키를 깃헙에 업로드하고 검증하는 작업이다.

익숙해지면 SSH가 더 편할것 같음

**SSH 주의사항**  
`ssh-keygen`으로 키를 만들고 나서 파일이름을 바꾸면 이상하게 인증이 안됨 (아직 해결 못함)

# 수정할 점
- ssh 알고리즘 `rsa`보다 `ed25519`가 더 안전함
- `-f` 옵션으로 파일 생성할 떄는 현재 디렉토리에 생성됨. 그러므로 `~/.ssh` 디렉토리를 지정하거나 `.ssh`에 들어가서 생성해야 함
- 마지막에 .ssh/config도 설정해주고
- `eval "$(ssh-agent -s)"`로 실행한다음 `ssh-add "개인키"`로 등록 해야 함
- pubkey 파일 복사하려면 파일 다운로드 받아서 복사해서 github에 넣어야 함 (또는 linux에서 cat으로 출력 한다음 엔터키까지 복사해야 함). 밑은 예시
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCsdcsEpMr1KCfVVFEh/g17RBH+xi2oddd abc@gmail.com
```

# 에러 핸들링
```
git@github.com: Permission denied (publickey). fatal: Could not read from remote repository.

Please make sure you have the correct access rights and the repository exists.
```
위와 같은 에러나면 `eval "$(ssh-agent -s)"`로 실행한다음 `ssh-add "개인키"`로 등록 해야 함



# 블로그에서 참고한 곳
- [한국 블로그 설명](https://usingu.co.kr/frontend/git/%ED%95%9C-%EC%BB%B4%ED%93%A8%ED%84%B0%EC%97%90%EC%84%9C-github-%EA%B3%84%EC%A0%95-%EC%97%AC%EB%9F%AC%EA%B0%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/)
- [Connect width SSH – GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [ssh_config(5): OpenSSH SSH client config files – Linux man page](https://linux.die.net/man/5/ssh_config)
- [Using the SSH Config File | Linuxize](https://linuxize.com/post/using-the-ssh-config-file/)

---

# 상세 튜토리얼
<details>
  <summary>클릭해서 펼치기</summary>

# How To Work With Multiple Github Accounts on a single Machine

Let suppose I have two github accounts, **https:/<span></span>/github.com<span></span>/rahul-office** and **https:/<span></span>/github.com<span></span>/rahul-personal**. Now i want to setup my mac to easily talk to both the github accounts.

> NOTE: This logic can be extended to more than two accounts also. :)

The setup can be done in 5 easy steps:
## Steps:
- [Step 1](#step-1) : Create SSH keys for all accounts
- [Step 2](#step-2) : Add SSH keys to SSH Agent
- [Step 3](#step-3) : Add SSH public key to the Github
- [Step 4](#step-4) : Create a Config File and Make Host Entries
- [Step 5](#step-5) : Cloning GitHub repositories using different accounts

<br>

## Step 1
### Create SSH keys for all accounts
First make sure your current directory is your **.ssh** folder. (윈도우에선 Users/<나>/.ssh 에 있음)
```sh
     $ cd ~/.ssh
```
Syntax for generating unique ssh key for ann account is:
```sh
     ssh-keygen -t rsa -C "your-email-address" -f "github-username"
```
here,

**-C** stands for comment to help identify your ssh key

**-f** stands for the file name where your ssh key get saved


#### Now generating SSH keys for my two accounts
```sh
     ssh-keygen -t rsa -C "my_office_email@gmail.com" -f "github-rahul-office"
     ssh-keygen -t rsa -C "my_personal_email@gmail.com" -f "github-rahul-personal"
```

Notice here **rahul-office** and **rahul-work** are the username of my github accounts corresponding to **my_office_email<span></span>@gmail.com** and **my_personal_email<span></span>@gmail.com** email ids respectively.

After entering the command the terminal will ask for passphrase, leave it empty and proceed.

![Passphrase Image](https://raw.githubusercontent.com/rahularity/github-essentials/bc3dafc37b36f5fb4ebcffcba63a7689a36fc7ff/screenshots/passphrase.png)

> Now after adding keys , in your .ssh folder, a public key and a private will get generated.

>The public key will have an extention __.pub__ and private key will be there without any extention both having same name which you have passed after __-f__ option in the above command. (in my case __github-rahul-office__ and __github-rahu-personal__)

![Added Key Image](https://raw.githubusercontent.com/rahularity/github-essentials/master/screenshots/ssh_keys_added.png)

<br>

## Step 2
### Add SSH keys to SSH Agent
Now we have the keys but it cannot be used until we add them to the SSH Agent.
```sh
     ssh-add -K ~/.ssh/github-rahul-office
     ssh-add -K ~/.ssh/github-rahul-personal
```

You can read more about adding keys to SSH Agent [here.](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

<br>

## Step 3
### Add SSH public key to the Github
For the next step we need to add our public key (that we have generated in our previous step) and add it to corresponding github accounts.

For doing this we need to:

__1. Copy the public key__

     We can copy the public key either by opening the github-rahul-office.pub file in vim and then copying the content of it.
```sh
     vim ~/.ssh/github-rahul-office.pub
     vim ~/.ssh/github-rahul-personal.pub
```

<p align="center">OR

We can directly copy the content of the public key file in the clipboard.

```sh
     pbcopy < ~/.ssh/github-rahul-office.pub
     pbcopy < ~/.ssh/github-rahul-personal.pub
```   


__2. Paste the public key on Github__

* Sign in to Github Account
* Goto **Settings** > **SSH and GPG keys** > **New SSH Key**
* Paste your copied public key and give it a Title of your choice.

___OR___

* Sign in to Github 
* Paste this link in your browser (https://github.com/settings/keys) or click [here](https://github.com/settings/keys)
* Click on **New SSH Key** and paste your copied key.

<br>

## Step 4
### Create a Config File and Make Host Entries

The **~/.ssh/config** file allows us specify many config options for SSH.

If **config** file not already exists then create one (make sure you are in **~/.ssh** directory)

```sh
     touch config
```

The commands below opens config in your default editor....Likely TextEdit, VS Code.
```sh
     open config
```
Now we need to add these lines to the file, each block corresponding to each account we created earlier.
```config
     #rahul-office account
     Host github.com-rahul-office
          HostName github.com
          User git
          IdentityFile ~/.ssh/github-rahul-office

     #rahul-personal account
     Host github.com-rahul-personal
          HostName github.com
          User git
          IdentityFile ~/.ssh/github-rahul-personal
```

<br>

## Step 5
### Cloning GitHub repositories using different accounts
(만약 clone이 필요없고 push부터 필요하면 여기는 필요없는 과정)

So we are done with our setups and now its time to see it in action. We will clone a repository using one of the account we have added.

Make a new project folder where you want to clone your repository and go to that directory from your terminal.

For Example:
I am making a repository on my personal github account and naming it **TestRepo**
Now for cloning the repo use the below command:
 ```git
     git clone git@github.com-{your-username}:{owner-user-name}/{the-repo-name}.git

     [e.g.] git clone git@github.com-rahul-personal:rahul-personal/TestRepo.git
 ```

 <br>

 ## Finally
 **알아둬야 할 사전 지식**
```
git config는 local과 global로 나뉨
local은 현재 폴더의 .git에 저장되고 global은 현재 폴더의 .git에 따로 명시 안할경우 사용되는 계정이다

- local 확인법: git config user.name|user.email|user.password
- global 확인법: git --global config user.name|user.email|user.password

(변경은 뒤에 "<content>" 로 넣으면 됨)

그래서 현재 작업한 결과들을 commit할 때 기준이 되는 user를 설정하는 작업이다 (local이 있으면 우선순위 높음)

그리고 아래 설명들은 2개의 계정을 따로 설정하는 법을 알려주는거라서 1개씩(위애꺼)만 하면 됨
```

From now on, to ensure that our commits and pushes from each repository on the system uses the correct GitHub user — we will have to configure **user.email** and **user.name** in every repository freshly cloned or existing before.

To do this use the following commands.

```git
     git config user.email "my_office_email@gmail.com"
     git config user.name "Rahul Pandey"
     
     git config user.email "my-personal-email@gmail.com"
     git config user.name "Rahul Pandey"
```
Pick the correct pair for your repository accordingly.


To push or pull to the correct account we need to add the remote origin to the project
```git
     git remote add origin git@github.com-rahul-personal:rahul-personal/<repo>.git
     
     git remote add origin git@github.com-rahul-office:rahul-office//<repo>.git
```
`만약 원래 origin이 있다면 remove하고 다시 추가`
`원래 <repo>.git을 안붙였는데 붙여야 됬었음`

Now you can use:
```git
     git push
     
     git pull
```
</details>