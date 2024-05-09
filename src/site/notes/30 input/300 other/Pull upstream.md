---
{"dg-publish":true,"permalink":"/30-input/300-other/pull-upstream/"}
---

[[30 input/300 other/Pull upstream\|Pull upstream]]
[[tags/Tech\|Tech]]

Git commands that enables you to pull changes from the repository that you forked from, aka "upstream".

```bash
cd PROJECT_NAME
$ git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
$ git fetch upstream

# then: (like "git pull" which is fetch + merge)
$ git merge upstream/master master

# or, better, replay your local work on top of the fetched branch
# like a "git pull --rebase"
$ git rebase upstream/master
```

---
- [b] [git - Pull new updates from original GitHub repository into forked GitHub repository - Stack Overflow](https://stackoverflow.com/questions/3903817/pull-new-updates-from-original-github-repository-into-forked-github-repository)
- tags: #coding 