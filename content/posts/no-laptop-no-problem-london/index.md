---
title: "No laptop, no problem: using Vim on my iPhone to write this article"
date: 2023-01-14T11:07:38+02:00
draft: false
author: "Robert Sandru"
tags: 
- Linux
- Terminal
- iPhone
cover:
  image: "images/london.jpeg"
---

This is the craziest stuff I ever did on my iPhone: writing this article using Vim.

I decided to have a city break in London this weekend. The plan was to disconnect a bit from technology, leaving my laptop at home to fully enjoy my two days off. I want to confess that today I walked ~20kms, so Saturday evening caught me exhausted in bed. Physically tired.

Tried to sleep, couldn't. My mind was constantly thinking about code, **what the hell**. One of the main points of my trip was to disconnect from tech. This was the moment I started to miss my laptop... 

Ok: no code environment, but how about writing on my blog? For a moment, I started to regret the fact that my blog is not Wordpress, as writing markdown articles using Hugo can be a pain on the go. Let's be real: the Wordpress app is so nice - UI is good, the editor is fantastic, everything a blogger needs. 

But what if I challenge myself to write an article using my iPhone? **brain: heavy breathing**. Writing an article for this blog means:

1. Cloning my GitHub repository where the Hugo project lives
2. Creating a new markdown post
3. Pushing changes to the main branch, where the GitHub workflow is going to use Hugo to build the static website

Well, sounds easy. Let's do that on mobile then. The first thing I thought about was to find an app to write MarkDown, then upload the file via the GitHub website and voila! 

Too easy. 

What I did instead:

1. Searched for some good apps that could give me some sort of Linux environment.

Found **LibTerm**, but it is incredibly limited. They offer some basic commands, without the ability of getting packages through some sort of package manager. 

Then I found iSH. This app is incredible. It comes with Alpine. ♥️ .

2. I needed Vim to write articles.

```bash
apk update
apk add vim
```

Boom. 

3. To clone my Hugo repo, I had to get git working.

```bash
apk add git
git config --global user.email "email"
git config --global user.name "name"
```

4. I wanted to use SSH to be able to fetch/push.

```bash
apk add openssh
ssh-keygen
```

Generated a key and added it to my GitHub profile.

5. Cloned the git repo to my phone. Had some issues with that, the 3rd time it worked. Something weird happened with the UI of the app, but behind the scenes I guess it worked well.

6. Tried to get Hugo up and running, then I realized this wasn't necessary at all because having a watcher was completely useless on mobile.

7. Created my post manually through the CLI, and pushed the changes to my repo. GitHub actions immediately generated the static site and published it. Isn't this amazing?

*Checkpoint: just pushed the changes again just in case*

This iSH app is just out of this world, and I can't believe it's free. I remember using Termux back in the day on Android, and it was powerful, as I could host python django local servers on the phone. Didn't imagine iOS could have something similar, as the AppStore is pretty much restricted. Anyway, until further research, I'm going to invalidate the ssh key used to connect to my GitHub profile. I guess I can go to sleep now.
