# vssh

A faster, funkier alternative to `vagrant ssh`.

Updated for bash shell (v5.0.17)
Tested on Vagrant 2.2.18

Now includes multi-remote host access from the ssh_config


```
3.0.0
  Usage: 
    vssh [options] 

  -v    Print the vssh version
  -h    Display this message
  -r    Interactively generate a new vssh config (do this first!)

  or
    vssh remote_host [-c "command(s)"]

  -c  Execute this command on the remote host
```

## Install

### [Dobbin](https://github.com/shkm/dobbin)
```
dobbin add https://github.com/shkm/vssh vssh
```

### Homebrew

```
brew install shkm/brew/vssh
```

### Generic
Copy or symlink `vssh` to a place in your path.


## Features

### Fast

`vagrant ssh` is slow. `vssh` is fast.

On my 2014 Macbook Air:

```
$ time vssh
vssh  0.02s user 0.01s system

$ time vagrant ssh
vagrant ssh  2.18s user 0.43s system
```

On 96GB RAM, dual Intel Xeon E5504
Vagrant 2.2.18

```
time vagrant ssh control -c "exit"
Connection to 127.0.0.1 closed.

real    0m16.507s
user    0m5.251s
sys     0m2.911s


time ./vssh -c hostname control
control
Connection to 127.0.0.1 closed.

real    0m1.572s
user    0m0.028s
sys     0m0.011s
```

### `ssh_config`

`ssh_config` is populated if not found (this actually calls vagrant, and is therefore slow). if your box's ssh config changes, you can refresh this with `vssh --refresh`.


## Inspiration
- Too much waiting
- A repo with projects as submodules
- [vassh](https://github.com/xwp/vassh)

