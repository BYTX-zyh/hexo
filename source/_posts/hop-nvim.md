---
title: hop.nvim
date: 2023-05-15 20:23:14
tags: [neovim,nvim-plug]
category : nvim
---

## 简介

[hop.nvim](https://github.com/phaazon/hop.nvim) 是一个类似于 easymotion的插件。其功能为通过尽可能少的按键去来进行文本跳转。在允许跳转的位置会出现浮动字符，输入对应字符即可跳转到对应位置。


> 大多数情况下跳转字符的数量都少于三个，以便快速进行跳转。

## 快速入门

### 安装

使用包管理器进行安装后，调用`require'hop'.setup()` 以启动 hop 并载入默认配置。

> 关于详细的启动设置查看`:h hop.setup` 。


## Commands

hop 具有各种命令，均以 *Hop* 开头，例如`HopWord` `HopChar` 等，但是commands
只有一部分常用命令，一些不常用或者自定义的hop操作可以通过调用 lua api 实现。

hop的命令通常有如下四种变体：
- `Hop*BC` : run `Hop*` before the cursor.
- `Hop*AC` : run `Hop*` after the cursor.
- `Hop*CurrentLine`: run `Hop*` on the current line only.
- `Hop*MW`: run `Hop*` across all visible buffers.

这四种变体还可以组合出现，例如：

- `Hop*CurrentLineBC`: run `Hop*` both before the cursor and on the current line only.
- `Hop*CurrentLineAC`: run `Hop*` both after the cursor and on the current line only.

> https://github.com/phaazon/hop.nvim/wiki/Commands

### commands list

- `HopAnywhere` : 跳转任意位置，但是通常由于提示内容过度且需要按更多的键才能跳转。
- `HopChar1` ： 输入一个字符，而后根据提示跳转。
- `HopChar2` ： 输入两个字符，而后根据提示跳转。
- `HopLine` ： 跳转到可见行行首。
- `HopLineStart` : 跳转到可见行的首个非空字符。
- `HopVertical` ： 跳转当前列所在的其他行的位置。
- `HopPattern` ： 跳转到搜索的内容。
- `HopWord` ： 跳转到word位置。

## config

查看：https://github.com/phaazon/hop.nvim/wiki/Configuration

## 高级使用

每个 hop command 都是对 hop lua api的调用：

- `HopAnywhere`:`require'hop'.hint_anywhere()`
- `HopChar1`:`require'hop'.hint_char1()`
- `HopChar2`:`require'hop'.hint_char2()`
- `HopLine`:`require'hop'.hint_lines()`
- `HopLineStart`:`require'hop'.hint_lines_skip_whitespace()`
- `HopVertical`:`require'hop'.hint_vertical()`
- `HopPattern`:`require'hop'.hint_patterns()`
- `HopWord`:`require'hop'.hint_words()`

可以使用这些函数创建更多的复杂跳转，这些函数都接受一个参数`opts`，该参数与传递给`require'hop'.setup`的内容相同，但是其优先级比`setup`函数更高。

例如可以这样调用：`:lua require'hop'.hint_words({ keys = 'abcd' })`。



> 如果需要调用变体`BC`,`AC`,`CurrentLine`,`MW`,使用如下方式：
>- `Hop*BC`
> `require'hop'.*({ direction = require'hop.hint'.HintDirection.BEFORE_CURSOR })`
>- `Hop*AC`
>`require'hop'.*({ direction = require'hop.hint'.HintDirection.AFTER_CURSOR })`
>- `Hop*CurrentLine`
>`require'hop'.*({ current_line_only = true })`
>- `Hop*MW`
>`require'hop'.*({ multi_windows = true })`

> `:h hop-lua-api` 
> https://github.com/phaazon/hop.nvim/wiki/Advanced-Hop
> 一些高级使用示例查看：https://github.com/phaazon/hop.nvim/wiki/Advanced-Hop#building-advanced-hop-motions

