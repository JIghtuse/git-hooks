# git-hooks

## Usage
Put any of these files into your project's `.git/hooks` directory.
Rename it to `pre-commit` and allow execution. For example,

    cp ./pre-commit-linters ~/projects/secret/.git/hooks/pre-commit
    chmod +x ~/projects/secret/.git/hooks/pre-commit


Now, when you change some files in repository and try to commit these
changes, git will run this script right before commit. Cppcheck will scan
changed/new files in repository. If it finds some issues, script returns with
exit code 1, rejecting commit. Otherwise, script returns 0, and you can
actually commit your changes.

If script rejects your commit, but you still want to perform it (make sure you
know what you do), you can bypass it with `--no-verify` option:

    git commit -v --no-verify

## Contents

* [pre-commit-cppcheck](./pre-commit-cppcheck) - script checks C/C++ files with
Cppcheck. Now the most updated version lives in
[cppcheck repo](https://github.com/danmar/cppcheck/blob/master/tools/git-pre-commit-cppcheck).
* [pre-commit-linters](./pre-commit-linters) - launches linters for various
files in repository. For now: [cppcheck](http://cppcheck.sourceforge.net/)
for C/C++ files, [xmllint](http://xmlsoft.org/xmllint.html) for XML files,
and [shellcheck](http://www.shellcheck.net/) for shell scripts.
