
# git-unrealmodule

## Background

- You deploy code using git to a system where all the code must be committed inside the repository
- You want to share code between your projects
- You cannot or do not want to use git submodule

Unrealmodules can help you in this situation. `

## Usage

Start with

1. Define a list of sub repositories and paths in a `.unrealmodules` file
2. Commit `.unrealmodules` in to the parent repository
3. Clone the sub repositories using `git unrealmodule clone`
4. Work on the parent and/or cloned sub repositories
5. Commit the sub repositories to the parent repository with `git unrealmodule commit`

When a new developer comes to the project he/she does not have to care at all about
the Unrealmodules but if they want to commit code back to the sub repository upstreams
they can restore the `.git` directories for the Unrealmodules with `git unrealmodule restore`.

The restore command is pretty low level at the moment.
It only restores the `.git` directory to the branch defined in `.unrealmodules`.
So it's very likely to see changes in the sub repository if the upstream has new commits
since the last `git unrealmodule commit` call.

It's up to the developer to handle this situation. They can neither reset the sub repository
or commit changes from the parent repository to the sub repository.

## Install

The `git-unrealmodule` is just a single POSIX shell script.

Simplest way to install it is just to copy it to `/usr/local/bin` directory.

or you can use the prodived installer

    git clone https://github.com/epeli/git-unrealmodule
    cd git-unrealmodule
    sudo make install

or you can install it with npm

    npm install -g git-unrealmodule
