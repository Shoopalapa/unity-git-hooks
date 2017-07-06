# Unity Git Hooks (LFS Edition)

Git hooks for Unity project using Git LFS.

Unity adds meta files for any file or directory in Assets and they should be 
added to your repository alongside the asset itself. There are some 
situations where the meta files and the corresponding asset files or 
directories are inconsistent, which can then cause conflicts or just commit 
spam when a team is collabarating on the same code base.

Git LFS is recommended for any Unity project with graphical assets and this 
set of hooks will respect that decision and should play nicely.

## Features

- Stop committing if meta files and asset files and directories are
  inconsistent. If an asset file is added, its meta file and meta files of all
  its containing directories should also been added. If a asset file is
  deleted, its meta file and meta files of all its empty containing
  directories should also been deleted. When meta files are added/deleted,
  asset files and directories should also been consistent.
- Delete empty asset directories after checkout and merge. Unity keep
  generating meta file for empty asset directory, but git does not trace
  directory.

## Usage

Add the `post-checkout` `post-merge` and `pre-commit` files to .git/hooks in your
git repository. If you also have hooks defined in these files, append them to
existing files.
