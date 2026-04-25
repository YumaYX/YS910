---
layout: post
title: LVMへPhysical Device追加
category: "ディスク"
---

Logical Volume(マウントポイント)の領域を新規に追加したディスクを使って拡張する。

# 何ができるか？

- より大きな、多くのファイルの保存
- Logical Volume(マウントポイント)の領域拡張
- Volume Groupを新規追加ディスクへ拡張、共用

# 拡張手順

## Disk追加

物理的なディスク(sdb)を追加（接続）する。

## 拡張コマンド

新規追加デバイスに、Volume Groupを見せてやり、Logical Volume、ファイルシステムを順に、拡張する。

```sh
df -h

pvcreate /dev/sdb
vgextend almalinux /dev/sdb
vgdisplay -v
lvextend -l +100%FREE /dev/almalinux/var
xfs_growfs /dev/almalinux/var

df -h
```

パーティションを切った場合の検証は実施していない。

# 書き込みチェック

```sh
cd /var
# /varに15GB書き込み
for f in $(seq 15); do dd if=/dev/random of=1G.dummy.$f bs=1M count=1000; df -h; done
rm -i 1G.dummy.*
```

rebootしても、拡張されている状態である(/etc/fstab -> /dev/mapper/vg-lv -> sda + sdb)。

# env.

```
AlmaLinux release 9.4 (Seafoam Ocelot)
```

# Reference

[新しいHDDを追加して既存LVM領域を拡張する手順メモ #Linux - Qiita](https://qiita.com/tomozo6/items/cdfb3ebc4be8bd19a2c9)
