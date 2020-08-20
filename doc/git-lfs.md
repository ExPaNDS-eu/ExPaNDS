# Git LFS

## Introduction

**Git LFS** is an extension pack for Git version control system. It is implemented on the top of Git itself as a set of helper programs. They provide for the given local copy of the Git repository a set of predefined procedures (so called *hooks*) allowing to avoid re-hashing of large binary objects ("blobs" here and below). Cause the original Git utilizes multihashes joining the data into the repository into content-based direct acyclic graphs with high proven integrity every piece of data added to the repository is compressed, assigned with Object ID (OID) and stored for the whole repository lifecycle. Thus adding and rehashing of the blobs bloat the repository itself and the most important problem is that it consumes resources during re-hashing of the blobs building OIDs.

As it is described in details in [the official documentation](https://github.com/git-lfs/git-lfs/blob/master/docs/spec.md), Git LFS assigns its own internal IDs to the blobs using one of existing [multihash](https://github.com/moreati/multihash/tree/spec) implementations. After that the blobs inside the repository are replaced by impostor text files containing metadata for building URI pointing to the actual data. Then Git LFS places the binary data of the blobs into special subdirectory within the repository and defines the filters to intercept the regular Git operations accessing these data. It leads to increasing of performance on both the local machine and remote Git server. However, on the server side Git LFS requires presence of special LFS daemon to parse requests operating with blobs as binary data streams. Implementations of such daemons are included into most popular web-based Git repository governors: [GitLab](https://gitlab.com/), [GitHub](https://github.com/), [Gerrit](https://gerritcodereview.com/) and others.

## Installation

In Ubuntu-based Linux distributions starting from version 18.04 there is a simple way to install Git LFS extension through `apt`:
```bash
sudo apt install git-lfs
```

For non-Debian based distributions the best way to install Git LFS is to compile it from sources as it is described in [official documentation](https://git-lfs.github.com/).

After the  successful installation the full set of LFS-related Git commands will become available under `lfs` prefix in the following form: `git lfs <command>`. For example:
```bash
git lfs clone
git lfs status
git lfs track
```

To retrieve detailed description for the given command the `--help` option can be added to the Git command line.

## Brief instruction manual

Git LFS, even in the case whe it is supported on the server side (on GitHub for example) requires initializaton of the hook set within each local repository it operates on. To install the LFS hooks into the cloned repository the `install` command should be used:
```bash
git lfs install
```
This command should be used for each LFS repository after the initial cloning. To uninstall the LFS hooks the `uninstall` command should be used.

After initialization the list of filesystem globals should be defined for the repository. This operations is performed by `track` LFS command. It places its output to [`.gitattributes`](../.gitattributes) service file. The command
```bash
git lfs track "*.png"
```
produces the following record:
```
*.png filter=lfs diff=lfs merge=lfs -text
```
in the `.gitattributes` file. Such records can be added to the `.gitattributes` file also manually.

After LFS support is properly initialized for the given repository, any file matching FS pattern mentioned in `.gitattributes` will be replaced with impostor file with the same name containing LFS pointer record (the example is given here for [README](../README) file of this repository):
```
README.md

version https://git-lfs.github.com/spec/v1
oid sha256:1f67d13eb29e7c955eb252e06e76f6c0aec66af23c2570cca397ad5191a2544f
size 2315
```

### Command list

In the following table the most used LFS commands are collected as they are described in the [official documentation](https://github.com/git-lfs/git-lfs/blob/master/docs/man/git-lfs.1.ronn)

|**Command**|**Description**|
|-----------|---------------|
|`git lfs env`|Displays the Git LFS environment variables|
|`git lfs checkout`|Populates local copy of the repository with real content from Git LFS OIDs|
|`git lfs dedup`|Deduplicates storage by re-creating working tree files as clones of the files in the Git LFS storage directory using the operating system's copy-on-write file creation functionality.|
|`git lfs ext`|Display Git LFS extension details (for the given command)|
|`git lfs fetch`|Downloads Git LFS objects at the given refs from the specified or default remote URI|
|`git lfs fsck`|Checks all LFS files in the current local repository state for consistency|
|`git lfs install`|Ensures that Git LFS is setup properly for the current repository|
|`git lfs logs`|Displays errors from the `git lfs` command.  Any time it crashes, the details are saved to `.git/lfs/logs`|
|`git lfs ls-files`|Displays paths of LFS files that are found in the tree at the given reference.  If no reference is given, scan the currently checked-out branch. If two references are given, the LFS files that are modified between the two references are shown, deletions are not listed.|
|`git lfs migrate info`|Show information about repository size|
|`git lfs migrate import`|Converts large Git objects to LFS pointers|
|`git lfs prune`|Deletes local copies of LFS files which are old enough. The command operates by enumerating all the locally stored objects, and then deleting any which are not referenced by at least one of the following sources: the *current* checkout, *recent* branch, *recent* commit of the *current* branch, most recent unpushed commit, last checkout of the worktree|
|`git lfs pull`|Downloads LFS objects for the currently checked out reference, updates the tree with the downloaded content if required, as an equivalent of the `fetch` and `checkout` LFS commands run in sequence|
|`git lfs push`|Upload LFS files to the configured endpoint for the current Git remote. By default, it filters out objects that are already referenced by the local copy of the repository|
|`git lfs status`|Show the status of Git LFS files in the working tree|
|`git lfs track`|Starts tracking the given FS patterns(s) through Git LFS|
|`git lfs uninstall`|Uninstall Git LFS from the repository by removing installed hooks and filters|
|`git lfs untrack`|Stops tracking the given FS patterns(s) through Git LFS|
|`git lfs update`|Updates the Git hooks used by Git LFS. Silently upgrades known hook contents|



