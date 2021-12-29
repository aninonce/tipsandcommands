# Git commands

### Contribution Guidelines

1. Fork -> Clone the project.
2. Make change.
3. Raise pull request & merge.


## Executing Git on command line
Commands below assume that git is installed / available + accessible on target system.

## Stages of git

```text
Git Directory:
	Where Git stores the metadata and object database for the repository. It is .git directory.
Working Directory:
	A copy of one version of the git project, taken from compressed database in the .git directory
Staging Area/Index:
	File that stores information about what will next be committed into the git repository 
```

#### How to execute
Options are allowed before and after task names.
```text
git [commandName...] [-option-name...]
git remote -v  // e.g.
```

#### Git help

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

#### Auto completion of git command
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

#### Check git version

```text
git --version
```
<details>
  <summary>Sample output: </summary>
  
  ```text
git version 2.25.1
```

</details>

#### Open man page for a git command

```text
git <commandName> --help
git branch --help  // Will open manual page for branch command
```

<details>
  <summary>Sample output: </summary>

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

<details>
  <summary>Sample output: </summary>

```text
error: unknown switch `p'
usage: git branch [<options>] [-r | -a] [--merged | --no-merged]
   or: git branch [<options>] [-l] [-f] <branch-name> [<start-point>]
   or: git branch [<options>] [-r] (-d | -D) <branch-name>...
   or: git branch [<options>] (-m | -M) [<old-branch>] <new-branch>
   or: git branch [<options>] (-c | -C) [<old-branch>] <new-branch>
   or: git branch [<options>] [-r | -a] [--points-at]
   or: git branch [<options>] [-r | -a] [--format]

Generic options
    -v, --verbose         show hash and subject, give twice for upstream branch
    -q, --quiet           suppress informational messages
    -t, --track           set up tracking mode (see git-pull(1))
    -u, --set-upstream-to <upstream>
                          change the upstream info
    --unset-upstream      unset the upstream info
    --color[=<when>]      use colored output
    -r, --remotes         act on remote-tracking branches
    --contains <commit>   print only branches that contain the commit
    --no-contains <commit>
                          print only branches that don't contain the commit
    --abbrev[=<n>]        use <n> digits to display SHA-1s

Specific git-branch actions:
    -a, --all             list both remote-tracking and local branches
    -d, --delete          delete fully merged branch
    -D                    delete branch (even if not merged)
    -m, --move            move/rename a branch and its reflog
    -M                    move/rename a branch, even if target exists
    -c, --copy            copy a branch and its reflog
    -C                    copy a branch, even if target exists
    -l, --list            list branch names
    --show-current        show current branch name
    --create-reflog       create the branch's reflog
    --edit-description    edit the description for the branch
    -f, --force           force creation, move/rename, deletion
    --merged <commit>     print only branches that are merged
    --no-merged <commit>  print only branches that are not merged
    --column[=<style>]    list branches in columns
    --sort <key>          field name to sort on
    --points-at <object>  print only branches of the object
    -i, --ignore-case     sorting and filtering are case insensitive
    --format <format>     format to use for the output
```
</details>

#### List all local branches in repo
```text
git branch
```

<details>
  <summary>Sample output: </summary>

```text
* master
```
</details>

#### Show hash, subject and remote repos of local branches

```text
git branch -v  // git branch --version
```

<details>
  <summary>Sample output: </summary>

```text
* master 3cb21589 Merge pull request #1904 from Netflix/qiangdavidliu-update-hystrix-status
```
</details>

#### List both local branches and remote tracking
```text
git branch -a  // git branch --all
```
<details>
    <summary>Sample output: </summary>

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

#### Create a new branch
```text
git branch [branchName]
git branch mybranch  // e.g.
```

### Delete a branch
```text
git branch -d [branchName]  // use -f option to force delete branch (in case branch has staging changes; make sure to double check / save / merge changes before deleting a branch)
git branch -d mybranch  // e.g.
```

<details>
    <summary>Sample output: </summary>

```text
Deleted branch mybranch (was 3cb21589).
```

</details>

#### Switching to new branch
```text
git checkout [branchName]  // you might need to stash / commit / discard changes in current branch before switching to new branch
git checkout mybranch  // e.g.
```

<details>
    <summary>Sample output: </summary>

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

#### Show commit logs
Most of the options for git log and git shortlog are same.
Below is list of few commands. For complete list of commands and usage check man page: git log --help.
```text
git log
git log | grep -i "show"  // Grep for specific word / expression
git log | grep -E "^commit"  // Show just the commit line; any grep expression can be used
git log --author=<name or email>  // Show git commits by an author
git log --skip=<number>  // Skip number commits before starting to show the commit output.
git log --reverse // Git commit log from beginging to end
git log --oneline // Git log in one line
git log --since=<date>, --after=<date> // Show commits more recent than a specific date.
git log --until=<date>, --before=<date> // Show commits older than a specific date.
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
    <summary> git log --author "David Liu" --after "11/19/2018" </summary>

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

#### Summarize git log
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

#### List all remote repositories
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
