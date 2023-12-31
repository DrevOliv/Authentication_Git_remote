# Authentication_Git_remote


### This is how to add a github and gilab account to the same computer and how to handle authentication. Doing so with ssh keys

#### 1. Creating the public and private ssh key, one for github and one for gitlab
in the terminal, and replace "your_email@example.com" with your email address:

`ssh-keygen -t ed25519 -C "your_email@example.com"`

#### 2. Naming the keys and saving them:

When you get the prompt:

`Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM):`

Copy the "/Users/YOU/.ssh/id_ALGORITHM" and at the en enter for example _gitlab or _github to differentiate the two keys

Then of the prompt: 

```
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```

add a password if you want to password protect the use of the keys, (recommend dot doing it).

#### 3. Add the keys to github and gitlab

Now add the .pub keys to github and gitlab by going into the settings and clicking on ssh or ssh keys, then add each key for each remote

#### 4. Ssh config

Go to the home dir where the folder .ssh is. In the .ssh folder create the file `config`, for bash: `nano ~/.ssh/config`

In the config file, change and add:

```
# GitHub
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/github_rsa

# other remote
Host <remote hostname>
  HostName <remote hostname>
  User git
  IdentityFile <path to the private key>
```

Should be done now, to test run in the terminal: `ssh -T git@<remote hostname>`

