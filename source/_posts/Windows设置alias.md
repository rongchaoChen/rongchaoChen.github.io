---
title: windows 设置alias
categories: [windows]
---

## 创建 Powershell 立即加载配置

根目录创建一个`$PROFILE`文件, 该文件定义了自定义立即加载的设置

然后修改执行策略权限:

```bash
get-ExecutionPolicy -List
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned  // 默认这行其实undefined
```

然后以管理员权限修改 poweshell 来改变执行策略

```bash
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
```

## Set-Alias

```bash
Set-Alias
   [-Name] <string> // 你要设置的别名
   [-Value] <string> // 比如设置别名软件的路径
   [-Description <string>] // 别名描述
   [-Option <ScopedItemOptions>]
   [-PassThru]
   [-Scope <string>] // 指定别名的有效范围 : Global(全局), Local, Private(专用), Numbered scopes(编号范围), Scripts(脚本), 默认为Local(本地)
   [-Force]  // 使用 Force 参数可以更改或删除 Option 参数设置为 ReadOnly 的别名。
   [-WhatIf]  // 表示陨石
   [-Confirm] // 在运行 cmdlet 之前提示您进行确认。
   [<CommonParameters>]
```

## 查看别名

```bash
Get-Alias -Definition Get-ChildItem
Get-Alias 别名
```

## 创建别名

```bash
//  name 表示你设置的别名 value: 表示别名本身代表的操作
Set-Alias -Name list -Value Get-ChildItem

```
