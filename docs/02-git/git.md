## Why git?


* Version control
* Branching
* Collaboration using GitHub
* History tracking
* Rollback changes
* Merge code

## Setup

=== "Windows"
    - [Install Git for Windows](https://git-scm.com/download/win)
    - Install [VS Code](https://code.visualstudio.com/docs/setup/windows) and [GitLens](https://www.gitkraken.com/gitlens) add-on.
    - Install [Windows Terminal](https://aka.ms/terminal) for a better shell experience.

=== "WSL"
    - [Install WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
    - [Linux basics](https://info-ee.surrey.ac.uk/Teaching/Unix/)
    - [Install Git to WSL Ubuntu](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-git#installing-git)
    - Install [VS Code in WSL Ubuntu](https://code.visualstudio.com/docs/setup/linux#_install-vs-code-on-linux) and [GitLens](https://www.gitkraken.com/gitlens) add-on.

=== "Linux"
    - [Linux basics](https://info-ee.surrey.ac.uk/Teaching/Unix/)
    - [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
    - Install [VS Code](https://code.visualstudio.com/docs/setup/linux) and [GitLens](https://www.gitkraken.com/gitlens) add-on.

## Setup and Configuration

```shell
git --version                               # Determine version number
git config --global user.name Yongjin Choi  # Set up configuration with name
git config --global user.email yj@mail.com  # Set up configuration with email
git config --list                           # Confirm and view changes
```

## Getting Help

```shell
git help <verb>                             # For example: git help config
git <verb> --help                           # For example: git config --help
```


## References
> * [https://learngitbranching.js.org/](https://learngitbranching.js.org/)
> * [https://jpvantassel.github.io/git-course/#/intro/getting_started](https://jpvantassel.github.io/git-course/#/intro/getting_started)
