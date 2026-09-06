  * Fixed bug where concurrent access to the virtual filesystem would cause
    a runtime panic.

v0.5.1
------

  * Fixed bug with database initialization when .tmsu directory does not
    already exist.

v0.5.0
------

  *Note: This release has some important changes, including the renaming of
  some options, the introduction of local databases and a switch from absolute
  to relative paths in the database. Please read the following release notes
  carefully.*

  * The --untagged option on the 'files' and 'status' subcommands has been
    replaced by a new 'untagged' subcommand, which should be more intuitive.
  * The --all option on the 'files', 'tags' and 'values' subcommands has been
    removed. These commands now list the full set of files/tags/values when run
    without arguments. For the 'tags' subcommand this replaces the previous
    behaviour of listing tags for the files in the working directory: use 'tmsu
    tags *' for approximately the previous behaviour.
  * The 'repair' subcommand --pretend short option has changed from -p to -P (so
    that -p can be recycled for --path).
  * The 'repair' subcommand's argument now specify paths to search for moved
    files and no longer limit how much of the database is repaired. A new --path
    argument is provided for reducing the repair to a portion of the database.
  * A new --manual option on the 'repair' subcommand allows targetted repair of
    moved files or directories.
  * The exclamation mark character (!) is no longer permitted within a tag or
    value name. Please rename tags using the 'rename' command. (Value names will
    need to be updated manually using the Sqlite3 tooling.)
  * Added --colour option to the 'tags' subcommand to highlight implied tags.
  * 'tag' subcommand will, by default, no longer explicitly apply tags that are
    already implied (unless the new --explicit option is specified).
  * Added subcommand aliases, e.g. 'query' for 'files'.
  * It is now possible to tag a broken symbolic link: instead of an error this
    will now be reported as a warning.
  * It is now possible to remove tags with values via the VFS.
  * 'tag' subcommand can tag multiple files with different tags by reading from
    standard input by passing an argument of '-'.
  * TMSU will now automatically use a local database in .tmsu/db in working
    directory or any parent. The new 'init' subcommand allows a new local
    database to be initialized. See [Switching Databases](https://github.com/oniony/TMSU/wiki/Switching%20Databases).
  * Paths are now stored relative to the .tmsu directory's parent rather than as
    absolute paths. This allows a branch of the filesystem to be moved around,
    shared or archived whilst preserving the tagging information. Existing
    absolute paths can be converted by running a manual repair:

        tmsu repair --manual / /

  * Added 'config' subcommand to view and amend settings.
  * The 'help' subcommand now wraps textual output to fit the terminal.
  * Rudimentary Microsoft Windows support (no virtual filesystem yet).
  * TMSU can now be built without the Makefile.
  * Bug fixes.
