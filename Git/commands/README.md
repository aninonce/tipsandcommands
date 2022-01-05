# Git commands

<a id="toc"></a>
## Table of contents

1. [Contribution guidelines](#contri_guidelines)
1. [Executing git commands via command line](#exec_cmd)
1. [Git directories](#git_direc)
1. [How to execute](#how_to_exec)
1. [Git help](#git_help)
1. [Auto completion](#auto_comp)
1. [Git version](#git_vesion)
1. [Git manual for a command](#git_man)
1. [Git branch & repo](#git_branch_&_repo)
    1. [List all local branches in repo](#git_local_branches)
    1. [List all remote repositories](#git_remote_repo)
    1. [Show hash, subject and remote repos of local branches](#git_local_branch_info)
    1. [Create a new branch](#git_branch_create)
    1. [Delete a branch](#git_branch_delete)
    1. [Switching to a branch](#git_branch_switch)
1. [Git tags](#git_tag)
    1. [Show all tags](#git_tag_all)
    1. [Create, delete push to repo tag](#git_tag_crud)
1. [Git log](#git_log)
    1. [Show commit logs](#git_log_show_commit)
    1. [Summarize git log](#git_log_summary)
1. [Working with git commits](#git_working_with_commit)
    1. [Git cherrypick](#git_cherrypick)
    1. [Remove, squash, rebase commits](#git_commit_crud)
    1. [Git merge](#git_merge)


<a id="contri_guidelines"></a>
### Contribution guidelines [^](#toc)

1. Fork -> Clone the project.
2. Make change.
3. Raise pull request & merge.

<a id="exec_cmd"></a>
## Executing git commands via command line  [^](#toc)
Commands below assume that git is installed / available + accessible on target system.

<a id="git_direc"></a>
## Git directories [^](#toc)


```text
Git Directory:
	Where Git stores the metadata and object database for the repository. It is .git directory.
Working Directory:
	A copy of one version of the git project, taken from compressed database in the .git directory
Staging Area/Index:
	File that stores information about what will next be committed into the git repository 
```

<a id="how_to_exec"></a>
## How to execute [^](#toc)
Options are allowed before and after task names.
```text
git [commandName...] [-option-name...]
git remote -v  // e.g.
```

<a id="git_help"></a>
## Git help [^](#toc)

```text
git help // is same as git --help
git help -a // To get list of all git commands
```

<details>
<summary>Sample output: git help </summary>

```text
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone             Clone a repository into a new directory
   init              Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add               Add file contents to the index
   mv                Move or rename a file, a directory, or a symlink
   restore           Restore working tree files
   rm                Remove files from the working tree and from the index
   sparse-checkout   Initialize and modify the sparse-checkout

examine the history and state (see also: git help revisions)
   bisect            Use binary search to find the commit that introduced a bug
   diff              Show changes between commits, commit and working tree, etc
   grep              Print lines matching a pattern
   log               Show commit logs
   show              Show various types of objects
   status            Show the working tree status

grow, mark and tweak your common history
   branch            List, create, or delete branches
   commit            Record changes to the repository
   merge             Join two or more development histories together
   rebase            Reapply commits on top of another base tip
   reset             Reset current HEAD to the specified state
   switch            Switch branches
   tag               Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch             Download objects and refs from another repository
   pull              Fetch from and integrate with another repository or a local branch
   push              Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.
```

</details>

<details>
<summary>Sample output: git help -a </summary>

```text
See 'git help <command>' to read about a specific subcommand

Main Porcelain Commands
   add                  Add file contents to the index
   am                   Apply a series of patches from a mailbox
   archive              Create an archive of files from a named tree
   bisect               Use binary search to find the commit that introduced a bug
   branch               List, create, or delete branches
   bundle               Move objects and refs by archive
   checkout             Switch branches or restore working tree files
   cherry-pick          Apply the changes introduced by some existing commits
   citool               Graphical alternative to git-commit
   clean                Remove untracked files from the working tree
   clone                Clone a repository into a new directory
   commit               Record changes to the repository
   describe             Give an object a human readable name based on an available ref
   diff                 Show changes between commits, commit and working tree, etc
   fetch                Download objects and refs from another repository
   format-patch         Prepare patches for e-mail submission
   gc                   Cleanup unnecessary files and optimize the local repository
   gitk                 The Git repository browser
   grep                 Print lines matching a pattern
   gui                  A portable graphical interface to Git
   init                 Create an empty Git repository or reinitialize an existing one
   log                  Show commit logs
   merge                Join two or more development histories together
   mv                   Move or rename a file, a directory, or a symlink
   notes                Add or inspect object notes
   pull                 Fetch from and integrate with another repository or a local branch
   push                 Update remote refs along with associated objects
   range-diff           Compare two commit ranges (e.g. two versions of a branch)
   rebase               Reapply commits on top of another base tip
   reset                Reset current HEAD to the specified state
   restore              Restore working tree files
   revert               Revert some existing commits
   rm                   Remove files from the working tree and from the index
   shortlog             Summarize 'git log' output
   show                 Show various types of objects
   sparse-checkout      Initialize and modify the sparse-checkout
   stash                Stash the changes in a dirty working directory away
   status               Show the working tree status
   submodule            Initialize, update or inspect submodules
   switch               Switch branches
   tag                  Create, list, delete or verify a tag object signed with GPG
   worktree             Manage multiple working trees

Ancillary Commands / Manipulators
   config               Get and set repository or global options
   fast-export          Git data exporter
   fast-import          Backend for fast Git data importers
   filter-branch        Rewrite branches

   .... more commands
```

</details>

<a id="auto_comp"></a>
## Auto completion of git command [^](#toc)
Git support auto completion for commands and options. While writing a command / option tap TAB key once / twice.
Auto completion of relevant option will work with the righ command
E.g.
```text
git br // Press TAB key once
git b  // Press TAB key twice consecutively
git log --i // Press TAB key twice consecutively
```

<details>
  <summary>Sample output: git br </summary>
  
  ```text
git branch
```
</details>

<details>
  <summary>Sample output: git b </summary>
  
  ```text
bisect   blame    branch   bundle
```
</details>

<details>
  <summary>Sample output: git log --i </summary>
  
  ```text
--ignore-all-space      --ignore-blank-lines    --ignore-cr-at-eol      --ignore-space-at-eol   --ignore-space-change   --ignore-submodules     --indent-heuristic      --inter-hunk-context=   --invert-grep
```
</details>


<a id="git_version"></a>
## Git version [^](#toc)

```text
git --version
```
<details>
  <summary>Sample output: </summary>
  
  ```text
git version 2.25.1
```

</details>

<a id="git_man"></a>
## Git manual for a command [^](#toc)

```text
git help <commandName>
git help branch  // Will open manual page for branch command
```

<details>
  <summary>Sample output: git help branch </summary>

```text
GIT-BRANCH(1)                                                                                                  Git Manual                                                                                                 GIT-BRANCH(1)

NAME
       git-branch - List, create, or delete branches

SYNOPSIS
       git branch [--color[=<when>] | --no-color] [--show-current]
               [-v [--abbrev=<length> | --no-abbrev]]
               [--column[=<options>] | --no-column] [--sort=<key>]
               [(--merged | --no-merged) [<commit>]]
               [--contains [<commit]] [--no-contains [<commit>]]
               [--points-at <object>] [--format=<format>]
               [(-r | --remotes) | (-a | --all)]
               [--list] [<pattern>...]
       git branch [--track | --no-track] [-f] <branchname> [<start-point>]
       git branch (--set-upstream-to=<upstream> | -u <upstream>) [<branchname>]
       git branch --unset-upstream [<branchname>]
       git branch (-m | -M) [<oldbranch>] <newbranch>
       git branch (-c | -C) [<oldbranch>] <newbranch>
       git branch (-d | -D) [-r] <branchname>...
       git branch --edit-description [<branchname>]

DESCRIPTION
       If --list is given, or if there are no non-option arguments, existing branches are listed; the current branch will be highlighted in green and marked with an asterisk. Any branches checked out in linked worktrees will be
       highlighted in cyan and marked with a plus sign. Option -r causes the remote-tracking branches to be listed, and option -a shows both local and remote branches.

       If a <pattern> is given, it is used as a shell wildcard to restrict the output to matching branches. If multiple patterns are given, a branch is shown if it matches any of the patterns.

       Note that when providing a <pattern>, you must use --list; otherwise the command may be interpreted as branch creation.

       With --contains, shows only the branches that contain the named commit (in other words, the branches whose tip commits are descendants of the named commit), --no-contains inverts it. With --merged, only branches merged into
       the named commit (i.e. the branches whose tip commits are reachable from the named commit) will be listed. With --no-merged only branches not merged into the named commit will be listed. If the <commit> argument is missing
       it defaults to HEAD (i.e. the tip of the current branch).

       The command’s second form creates a new branch head named <branchname> which points to the current HEAD, or <start-point> if given. As a special case, for <start-point>, you may use "A...B" as a shortcut for the merge base
       of A and B if there is exactly one merge base. You can leave out at most one of A and B, in which case it defaults to HEAD.

       Note that this will create the new branch, but it will not switch the working tree to it; use "git switch <newbranch>" to switch to the new branch.
```
</details>

<a id="git_branch_&_repo"></a>
## Git branch & repo [^](#toc)

<a id="git_local_branches"></a>
### List all local branches in repo [^](#toc)
```text
git branch
```

<details>
  <summary>Sample output: </summary>

```text
* master
```
</details>

<a id="git_remote_repo"></a>
### List all remote repositories [^](#toc)
```text
git remote -v
```

<details>
    <summary>Sample output: </summary>

```text
origin  https://github.com/Netflix/Hystrix.git (fetch)
origin  https://github.com/Netflix/Hystrix.git (push)
```

</details>

<a id="git_local_branch_info"></a>
### Show hash, subject and remote repos of local branches [^](#toc)

```text
git branch -v  // git branch --version
```

<details>
  <summary>Sample output: </summary>

```text
* master 3cb21589 Merge pull request #1904 from Netflix/qiangdavidliu-update-hystrix-status
```
</details>

<a id="git_branch_info"></a>
### List both local branches and remote tracking [^](#toc)
```text
git branch -a  // git branch --all ; will show all branches local and remote
git branch -r  // list remote branches
git branch -av  // list all branches with remote repos
```
<details>
    <summary>Sample output: git branch -a </summary>

```text
* master
  remotes/origin/1.4.x
  remotes/origin/1.5.x
  remotes/origin/2.0.x
  remotes/origin/HEAD -> origin/master
  remotes/origin/contributing
  remotes/origin/disable_tests
  remotes/origin/gh-pages
  remotes/origin/master
  remotes/origin/publish_via_travis
  remotes/origin/qiangdavidliu-update-hystrix-status
  remotes/origin/travis-ci-com
```

</details>

<details>
    <summary>Sample output: git branch -r </summary>

```text
  remotes/origin/1.4.x
  remotes/origin/1.5.x
  remotes/origin/2.0.x
  remotes/origin/HEAD -> origin/master
  remotes/origin/contributing
  remotes/origin/disable_tests
  remotes/origin/gh-pages
  remotes/origin/master
  remotes/origin/publish_via_travis
  remotes/origin/qiangdavidliu-update-hystrix-status
  remotes/origin/travis-ci-com
```

</details>

<details>
    <summary>Sample output: git branch -av </summary>

```text
* master                                             3cb21589 Merge pull request #1904 from Netflix/qiangdavidliu-update-hystrix-status
  remotes/origin/1.4.x                               00bed20c Merge pull request #1527 from Psynbiotik/patch-1
  remotes/origin/1.5.x                               809104c8 Merge pull request #1901 from Netflix/publish_via_travis
```

</details>

<a id="git_branch_create"></a>
### Create a new branch [^](#toc)
```text
git branch <branchName>
git branch mybranch  // e.g.
git branch <branchName> <tagName>  // create branch from a tag
git branch <branchName> <commitSHA>  // create branch from a commitSHA. Get commitSHA from command 'git log' or 'git log --oneline'
git push origin <branchName>  // will push the branch to remote
```

<a id="git_branch_delete"></a>
### Delete a branch [^](#toc)
```text
git branch -d <branchName>  // use -f option to force delete branch (in case branch has staging changes; make sure to double check / save / merge changes before deleting a branch)
git branch -d mybranch  // e.g.
git push origin -d <remoteBranchName> // will delete the remote branch
```

<details>
    <summary>Sample output: </summary>

```text
Deleted branch mybranch (was 3cb21589).
```

</details>

<a id="git_branch_switch"></a>
### Switching to a branch [^](#toc)
```text
git checkout <branchName>  // you might need to stash / commit / discard changes in current branch before switching to new branch
git checkout mybranch  // e.g.
git checkout -b mybranch  // will create branch 'mybranch' and checkout i.e. switch to branch. -b stands for branch
git checkout -b mybranch <tagName> // create branch 'mybranch' from tag <tagName>
git branch <branchName> <commitSHA>  // create branch from a commitSHA. Get commitSHA from command 'git log' or 'git log --oneline'
```

<details>
    <summary>Sample output: git checkout mybranch</summary>

```text
M       hystrix-serialization/src/main/java/com/netflix/hystrix/serial/SerialHystrixMetric.java
M       hystrix-serialization/src/main/java/com/netflix/hystrix/serial/SerialHystrixRequestEvents.java
M       hystrix-serialization/src/main/java/com/netflix/hystrix/serial/SerialHystrixUtilization.java
M       hystrix-serialization/src/test/java/com/netflix/hystrix/serial/SerialHystrixRequestEventsTest.java
M       settings.gradle
Switched to branch 'mybranch'

subsequent use of : 'git branch' command will show the branch as current branch (denoted by *)
  master
* mybranch
```

</details>

<a id="git_tag"></a>
## Git tags [^](#toc)
Tags are used as reference point in development.

<a id="git_tag_all"></a>
### Show all tags [^](#toc)
```text
git tag
git tag -n  // Show tag messages as well
```

<details>
    <summary>Sample output: git tag</summary>

```text
1.0.4
1.1.0
1.1.1
```

</details>

<details>
    <summary>Sample output: git tag -n </summary>

```text
v1.5.11         Release of 1.5.11
v1.5.12         Release of 1.5.12
```

</details>

<a id="git_tag_crud"></a>
### Create, delete, push to repo tag [^](#toc)
```text
git tag -a <tagName> -m "<message>"
git tag -a <tagName> <commitSHA> -m "<message>" // create a tag for specific commit. commitSHA can be obtained from 'git log --oneline' command.
git tag -d <tagName>  // will delete tag. Use -f for force delete
git push origin <tagName>  // will push tag to remote
```

<details>
    <summary>Sample output: git tag -d mytag</summary>

```text
Deleted tag 'mytag' (was d141f747)
```

</details>

<a id="git_log"></a>
## Git log [^](#toc)
Git log is record of commits as referenced from refs e.g. head, remote branch, tag
where as git reflog is record of all commits that were referenced in repo.
Git reflog is useful to get hash of commit (as long as commit is there in remote) in case of accidental damage to your repo.
Git reflog is purely local. If is not inluced in any push / fetch.
By default git reflog is maintained for 90 days.


<a id="git_log_show_commit"></a>
### Show commit logs [^](#toc)
Most of the options for git log and git shortlog are same.
Below is list of few commands. For complete list of commands and usage check man page: git log --help.
```text
git log
git log | grep -i "show"  // Grep for specific word / expression
git grep -i "show"  // Though normal grep can be used with pipe with any git command, it is better to use directly git grep command as it allow searching for expression in files in work tree. Usual grep options can be used. check 'git help grep' for git manual on grep
git log | grep -E "^commit"  // Show just the commit line; any grep expression can be used
git log --author=<name or email>  // Show git commits by an author
git log --skip=<number>  // Skip number commits before starting to show the commit output.
git log --reverse // Git commit log from beginging to end
git log --oneline // Git log in one line
git log --since=<date>, --after=<date> // Show commits more recent than a specific date.
git log --until=<date>, --before=<date> // Show commits older than a specific date.
git log --stat  // Get a diffstat i.e. what files where changed and how many lines changed in a 
commit.
git reflog
E.g
git log --author "David Liu" --after "11/19/2018"
git log --author "David Liu" --after "Nov 19 2018"
git log --author "David Liu" --before "Mon Nov 19 14:18:19 2018"
```

<details>
    <summary>Sample output: git log </summary>

```text
commit 3cb21589895e9f8f87cfcdbc9d96d9f63d48b848 (HEAD -> master, origin/master, origin/HEAD)
Merge: 7f5a0afc c0aae119
Author: Tim Bozarth <tim@zarthsan.com>
Date:   Mon Nov 19 14:20:36 2018 -0800

    Merge pull request #1904 from Netflix/qiangdavidliu-update-hystrix-status

    Update official Netflix Hystrix Status

commit c0aae119c00e2af24015eee8266a7882a89daa58 (origin/qiangdavidliu-update-hystrix-status)
Author: David Liu <qiang.david.liu@gmail.com>
Date:   Mon Nov 19 14:19:00 2018 -0800
```

</details>

<details>
    <summary>Sample output: git log | grep -E "^commit" </summary>

```text
commit 3cb21589895e9f8f87cfcdbc9d96d9f63d48b848
commit c0aae119c00e2af24015eee8266a7882a89daa58
commit a7df971cbaddd8c5e976b3cc5f14013fe6ad00e6
commit 7f5a0afc23aa5ff82320560a04d4c81a45efd67c
commit 86eb9458990d1d0f677ac4de920b4289d722e105
```

</details>

<details>
    <summary>Sample output: git log --author "Tim Bozarth" </summary>

```text
commit 3cb21589895e9f8f87cfcdbc9d96d9f63d48b848 (HEAD -> master, origin/master, origin/HEAD)
Merge: 7f5a0afc c0aae119
Author: Tim Bozarth <tim@zarthsan.com>
Date:   Mon Nov 19 14:20:36 2018 -0800

    Merge pull request #1904 from Netflix/qiangdavidliu-update-hystrix-status

    Update official Netflix Hystrix Status

commit 7f5a0afc23aa5ff82320560a04d4c81a45efd67c
Merge: 7184bdc6 86eb9458
Author: Tim Bozarth <tim@zarthsan.com>
Date:   Fri May 4 15:36:18 2018 -0700

    Merge pull request #1797 from MenschNestor/master

    Stabilize yet another test

commit 6fd44d7d96bbe93266146371acc9bae64085d06c
Merge: 255a569b 840e63c6
Author: Tim Bozarth <tim@zarthsan.com>
Date:   Tue Apr 24 11:00:27 2018 -0700

    Merge pull request #1786 from MenschNestor/master

    Stabilize another test
```

</details>

<details>
    <summary>Sample output: git log --stat </summary>

```text
commit 1fd939b83caa7823d78476369955177313155c59
Author: Christoph Seibert <christoph.seibert@rewe-digital.com>
Date:   Wed Apr 4 19:21:59 2018 +0200

    Reduced number of concurrent connections because there is a limit depending on the number of available cores times 2 in Grizzly's NetworkListener

 hystrix-contrib/hystrix-metrics-event-stream-jaxrs/src/test/java/com/netflix/hystrix/contrib/metrics/controller/HystricsMetricsControllerTest.java | 6 +++---
 hystrix-contrib/hystrix-metrics-event-stream-jaxrs/src/test/resources/test.properties                                                              | 3 ++-
```

</details>

<details>
    <summary>Sample output: git reflog </summary>

```text
3cb21589 (HEAD -> master, origin/master, origin/HEAD) HEAD@{0}: checkout: moving from mybranch to master
3cb21589 (HEAD -> master, origin/master, origin/HEAD) HEAD@{1}: checkout: moving from master to mybranch
```

</details>

<details>
    <summary>Sample output: git log --author "David Liu" --after "11/19/2018" </summary>

```text
Author: David Liu <qiang.david.liu@gmail.com>
Date:   Mon Nov 19 14:19:00 2018 -0800

    Update OSSMETADATA

commit a7df971cbaddd8c5e976b3cc5f14013fe6ad00e6
Author: David Liu <qiang.david.liu@gmail.com>
Date:   Mon Nov 19 14:18:19 2018 -0800

    Update README.md
```

</details>

<a id="git_log_summary"></a>
### Summarize git log [^](#toc)
Most of the options for git shortlog is same as git log.
Below is list of few commands. For complete list of commands and usage check man page: git shortlog --help.
```text
git shortlog
git shortlog -<number>, -n <number>, --max-count=<number>  // Limit the number of commits to output.
git shortlog -10 // e.g.
git log --author=<name or email>  // Show git commits by an author
git shortlog -se | sort -r  // Show commits by authors (name + email) in reverse order of total number of commits per author
git shortlog --skip=<number>  // Skip number commits before starting to show the commit output.
git shortlog --since=<date>, --after=<date> // Show commits more recent than a specific date.
git shortlog --until=<date>, --before=<date> // Show commits older than a specific date.
```
<details>
    <summary>Sample output: git shortlog </summary>

```text
Adam Gent (8):
      Make Archaius a soft dependency through reflection and improve plugin loading. See #970 #129 #252
      Fix documentation and some code cleanup.
      Added lazy loading and unit tests.
      Fix for backward compatibility with Hystrix 1.4
      Simplify chained properties and expose less public methods/classes.
      Fix unit test.
      Add system property to pick HystrixDynamicProperties and made Archaius Helper more private.
      Updates based on @mattrjacobs comments

Adriano Bonat (1):
      fixed the mock stream.

Alex Khomchenko (1):
      #1536 handle not wrapped exceptions same way as all other

Alexander Schwartz (4):
      deploying on tomcat, SLF4J complains about a missing implementation
      remove surplus closing curly brackets at end of file
      Internalize internet dependencies from hystrix dashboard
      Cleanup remaining Observables in Schedulers.computation() of RxJava after each test

Andreas Kluth (1):
      Updated outdated class names.
```

</details>

<details>
    <summary>Sample output: git shortlog -10 </summary>

```text
Christoph Seibert (4):
      Run command runnables on a single thread executor to get deterministic results
      Only check for thread isolation if the command had a chance to start executing
      Merge remote-tracking branch 'upstream/master'
      Again: Only check for thread isolation if the command had a chance to start executing

David Liu (2):
      Update README.md
      Update OSSMETADATA

David Robert Duke (1):
      Merge pull request #1757 from erichhsun/sse-sample-servlet-race-condition

Tim Bozarth (3):
      Merge pull request #1786 from MenschNestor/master
      Merge pull request #1797 from MenschNestor/master
      Merge pull request #1904 from Netflix/qiangdavidliu-update-hystrix-status
```

</details>

<details>
    <summary>Sample output: git shortlog --author "David Liu" </summary>

```text
David Liu (8):
      deprecated and move hystrix-dashboard to Netflix-skunkworks
      fix a flaky test
      increase timeout for a test
      add additional wait time in test to avoid flakiness on travisCI
      increase test time await for travisCI builds
      Merge pull request #1749 from qiangdavidliu/master
      Update README.md
      Update OSSMETADATA
```

</details>

<details>
    <summary>Sample output: git shortlog -se | sort -r </summary>

```text
   538  Matt Jacobs <mattrjacobs@gmail.com>
   523  Matt Jacobs <mjacobs@netflix.com>
   311  Ben Christensen <benjchristensen@gmail.com>
   208  Ben Christensen <benjchristensen@netflix.com>
    75  dmgcodevil <dmgcodevil@gmail.com>
    58  Bob T Builder <builds@netflix.com>
    50  Justin Ryan <jryan@netflix.com>
    24  Roman Pleshkov <dmgcodevil@gmail.com
```

</details>

<a id="git_working_with_commit"></a>
## Working with git commits [^](#toc)

<a id="git_cherrypick"></a>
### Git cherrypick [^](#toc)
Pick a commit (or commits) from a branch and applying it to another.
```text
1. git cherry-pick <list of commitSHA>  // Will apply list of commitSHA given to current branch. If the commit it already present in current branch it will be duplicated. User git rebase command to fix commits. Once commit (/ commits) are applied in current branch, they can be pushed by using git push command.

Use command 'git cherry-pick -e <list of commitSHA>'  // To modify commit message

E.g. 

Git branch state before cherry pick

a - b - c  master
    \
     d - e  feature

First make sure you are on branch where you want to add the cherry picked up commit

git checkout master

then do cherry picking of commit

git cherry-pick e

a - b - c - e  master
    \
    d - e  feature
```

<a id="git_commit_crud"></a>
### Remove, squash, rebase commits [^](#toc)
Squash - Merge multiple commits into single commit.
```text
1. git revert --strategy resolve <commitSHA>  // revert a specific commit. After reverting commit changes needs to be pushed using 'git push -f origin <branchName>' -f for using force option if push shows nothing to push.
2. Commits can be reverted using rebase as well.
git rebase -i HEAD~n  // n is number of commits. This will open an interactive window, 
where commits will be listed. Use respective commands in front of each commit for intended
action e.g. pick, squash, drop etc. Descritpion of each comamnd will be in the interactive 
rebase. Make change and save the rebase. Use command 'git push -f origin <branchName>' to push change to remote.
git rebase --abort  // If a mistake is made with rebase
```

<a id="git_merge"></a>
### Git merge [^](#toc)
Merge sequence of commits from one branch into another branch.
```text
E.g.

Before merge

      Branch A tip  
        |
a - b - c
|\
| d - e - f  
|         |
Base  Branch B tip 

After merge

Before merge

      Branch A tip  
        |
a - b - c -  g
|\         / |
| d - e - f  Merge commit
|         |
Base  Branch B tip

1. Check out the branch which you want to merge your code into
2. Use command 'git merge <branchName>'  // branchName - merge changes from this branch to current branch. This will create new commit in current branch. Then the new commit can be pushed with push command.
```