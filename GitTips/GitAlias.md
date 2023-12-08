## USEFUL GIT ALIAS

Open `~/.gitconfig` and add the following

```
[alias]
	st = status -sb
	ll = log --oneline
	last = log -1 HEAD --stat
	rv = remote -v
	d = diff
	graph = log --oneline --graph --decorate
	co = checkout
    del = branch -D   # delete a branch
    br = branch --format='%(HEAD) %(color:yellow)%(refname:short)%(color:reset) - %(contents:subject) %(color:green)(%(committerdate:relative)) [%(authorname)]' --sort=-committerdate
```




### CREDITS
https://snyk.io/blog/10-git-aliases-for-faster-and-productive-git-workflow/  
https://opensource.com/article/20/11/git-aliases