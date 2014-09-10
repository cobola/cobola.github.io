---
layout: post
title: use vboxmanage createvm with exist vdi
---



first ,use ftp or sftp copy the vdi file to the host.


clone
-----
> vboxmanage clonehd ../xp1/xp_with_editor.vdi xp4.vdi

register
-----

> vboxmanage createvm --name "xp4" --ostype WindowsXP --register


add storagectl
-----

> vboxmanage storageattach "xp4" --storagectl "IDE Controller" --port 0 --device 0 --type hdd --medium "xp4.vdi"

set memory and networks
-----

> vboxmanage modifyvm xp4 --memory 2048 --acpi on

> vboxmanage modifyvm xp4 --vram 256

> vboxmanage modifyvm xp4 --nic1 nat

> vboxmanage modifyvm  "xp4" --natpf1 "xp4mstsc,tcp,,9094,,3389"


start vm
-----

vboxmanage startvm xp4 --type headless



then you can use mstsc to login!



other usefull command
========

power off
---

> vboxmanage controlvm xp5 poweroff

delete
-----


> vboxmanage unregistervm xp5 --delete


resize

    vboxmanage modifyhd xp4.vdi --resize 100000

