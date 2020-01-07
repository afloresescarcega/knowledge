## pgrep

Allows you to look up PID of processes that match a critiera


### Formula
pgrep [options] pattern

```bash
pgrep -u root sshd
```
Will list the processes called sshd but only those that are owned by root


## pstree

Allows you to see the `tree` of a process and its children

### Formula
pstree pid

`-c` will show you the compact tree
`-p` will show you the pid and all the leaves
`-A` will show the tree with ascii character

