---
layout: post
title: Git tricks
date: 2013-03-01 13:45:40
author: Nick Boyce
---
About a year or so ago, I started keeping notes of my most-used Git tricks. I still refer back to them as I am so terrible at remembering commands (particularly unintuitive ones like deleting remote branches), so I thought they might be useful for others too.

---

Keep git from tracking permission changes to files
    git config core.filemode false

Restore a branch to the remote version (i.e. if you have pulled an incorrect remote branch)
    git fetch git reset --hard origin/master
  
Restore a single file to a version on another branch
    git checkout branch_name path/to-file    
  
Search for a string in the commit history:
    git show :/search_string  

Amend the last commit message:
    git commit --amend -m "New commit message"  

Toggle between branches
    git checkout -  

colourise all git commands
    git config --global color.ui true  

Use mergetool
    git mergetool -t opendiff

Delete a branch remotely 
    git push origin :newfeature

Delete a branch locally
    git branch -d newfeature  

Delete branches that don't exist on remote
    git remote prune origin
 
This one is Github-specific: You can compare commit ranges by appending compare like so...
    compare/master…someotherbranch
    compare/master@{yesterday}…master
    compare/master@{2.days.ago}…master
    compare/master@{2012-05-01}…master