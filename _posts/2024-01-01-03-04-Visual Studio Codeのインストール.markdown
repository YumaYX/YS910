---
layout: post
title: "Visual Studio Codeのインストール"
category: "パッケージレポジトリ"
---

Visual Studio Codeのインストールをインストールする。

## Visual Studio Codeのインストール

### インストール

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null

dnf check-update
sudo dnf -y install code
```

[Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions)


## sshリモート先のディレクトリを開く方法

1. VS Code左下の`><`のボタンをクリック
1. `SSH`を選択
1. `Add new host`を選択
1. `ssh -i <key> <user>@<hostname>`を入力

### 接続

1. VS Code左下の`><`のボタンをクリック
1. `SSH`を選択
1. ホストを選択して接続
