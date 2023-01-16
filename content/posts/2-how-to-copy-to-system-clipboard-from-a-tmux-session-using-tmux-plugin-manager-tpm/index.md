---
title: "How to Copy to System Clipboard From a Tmux Session Using Tmux Plugin 
Manager (TPM)"
date: 2021-09-23T03:07:38+02:00
draft: false
author: "Robert Sandru"
tags: 
- Linux
- Terminal
- Tmux
cover:
  image: "images/tmux.png"
---

One important thing people realize when they use tmux on a daily basis, is that
tmux has it’s own clipboard that you can’t use outside the software. It’s pretty inconvenient, as we usually copy-paste elements from our terminals to share with colleagues, search for problem solutions and so on.

Switching to the classic terminal is not a solution, or is it? No, it’s
definitely not.

The simplest solution for this issue is to install **tmux plugin manager**
that you can find on GitHub, alongside updated installation notes. The process
is simple:

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Create a new tmux configuration file in the home directory if you don’t have it already:

```bash
touch ~/.tmux.conf
```

We are going to use tmux-yank plugin to be able to copy directly to the system clipboard. Beside the main content tpm is offering for our `~/.tmux.conf`
file, we are also going to add tmux-yank. But before that, we must install
another program such as xclip that’s going to store data in the system
clipboard. I’m using xclip on my system.

```bash
sudo apt-get install xclip
```

Next, vim into the `~/.tmux.conf` file and add the following content:

```bash
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-yank'

run '~/.tmux/plugins/tpm/tpm'
```

Save the file, then open a new tmux session. In order to install plugins,
all you have to do is to use the `prefix + capital i` letter. My command prefix
is Ctrl + B on Ubuntu.

```bash
Ctrl+B + I
```

The TMUX environment will automatically reload then.

At this point, you should be able to select text and copy it into your
clipboard. For example, try to vim into your `~/.tmux.conf` file, go into the
copy text mode using `prefix+[`, select text with `prefix+SPACE` and then
just press `Y`. The text will be copied into the system clipboard.
