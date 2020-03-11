# multiple-ssh
* *Manage multiple ssh keys on 1 machine* *



**Generate 2 ssh keys:**
```
$ ssh-keygen -t rsa -C "personal@example.com" -f "id_rsa_personal"
$ ssh-keygen -t rsa -C "work@example.com" -f "id_rsa_work"
```


**Modify ssh config file (~/.ssh/config)**
```
Host github.com-personal
  IdentityFile ~/.ssh/id_rsa_personal
  HostName github.com
  User git

Host github.com-work
  IdentityFile ~/.ssh/id_rsa_work
  HostName github.com
  User git
```

**Verify ssh keys**
```
ssh -T git@github.com-personal
ssh -T git@github.com-work
```

**Move to your repository and change config information**
```
$ git config user.name "personal_username"
$ git config user.email "personal@example.com" 
$ git remote set-url origin git@github.com-personal:personal_username/repository-name.git
```
