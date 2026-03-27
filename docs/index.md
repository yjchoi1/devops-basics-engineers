# DevOps basics for Engineers

> [Yongjin Choi, KAIST](https://sites.google.com/view/geo-yjchoi/home)

## About This Guide
As an engineering researcher, I realized the importance and the challenges of systematic **version control** when developing research software, **collaborating** with other researchers, and handling **environment dependency** issues during software deployment. 

Fortunately, there are tools and workflows that make **these tasks much easier**. I made this learning module in the hope that it can help engineers and researchers who are new to these topics get started more easily and practically. It focuses on essential tools and workflows that support effective research code and software development.

## Prerequisite

* Install Git, VS Code, and GitLens extension.

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

* Create [Github](https://github.com/) account
* (Optional) Install [Docker](https://hub.docker.com/) and create [Dockerhub](https://hub.docker.com/) account