# Git

1. Create ssh key-pair with `ssh-keygen -t ed25519 -f ~/.ssh/<file name>`
2. Add public key to GitHub/GitLab/Huggingface/etc.
3. Add the following to `~/.ssh/config`.

```bash
# ~/.ssh/config

# github
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_github_ed25519 # filename will vary

# gitlab
Host gitlab.com
  HostName gitlab.com
  User git
  IdentityFile ~/.ssh/id_gitlab_ed25519 # filename will vary

# huggingface
Host hf.co
  HostName hf.co
  User git
  IdentityFile ~/.ssh/id_huggingface_ed25519 # filename will vary
```
