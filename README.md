# Dotfiles

My basic OS X dotfiles.
- [.bash_profile](https://github.com/cde/dotfiles/blob/master/bash/.bash_profile)
- [.gitconfig](https://github.com/cde/dotfiles/blob/master/git/.gitconfig)


## Custom  bash profile

**Homebrew**

I use the popular package manager one for OS X  [Homebrew](http://brew.sh/) to install (and update) applications for OS X or libraries for programing languages (mostly for ruby).

After installing ***Homebrew*** you need to tell the system to use programs installed by Homebrew rather than the OS default if it exists.
You do that by adding  /usr/local/bin to your $PATH environment variable:

    echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile

**rbenv**

I use [rbenv](https://github.com/rbenv/rbenv) to manage my Ruby versions.
After installing **rbenv** add it to your bash so that it loads every time you open a terminal

    echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
    source ~/.bash_profile

**Load bash setting files**

Add the bellow line to your login shell   ***.bash_profile***
    # Load the shell dotfiles, and then some:
    # * ~/.path can be used to extend `$PATH`.
    # * ~/.extra can be used for other settings you don’t want to commit.
    for file in ~/.{path,extra, bash_prompt,bash_aliases,  exports,functions}; do
      [ -r "$file" ] && source "$file"
    done
    unset file

You can load any setting file directly in your ***.bash_profile***. In my case I have [.bash_aliases](https://github.com/cde/dotfiles/blob/master/bash/.bash_aliases) and [.bash_prompt](https://github.com/cde/dotfiles/blob/master/bash/.bash_prompt)


### Custom bash prompt

On [iTerm2](http://www.iterm2.com/), I use a custom bash prompt based on the Solarized color palette and influenced by @necolas’s prompt.

Install [iTerm2](http://www.iterm2.com/) and under the section **Colors**, select **Color Presets** and select ***Solarized Dark theme*** if you like to follow this.


When your current working directory is a Git repository, the prompt will
display the checked-out branch's name (and failing that, the commit SHA that
HEAD is pointing to). The state of the working tree is reflected in the
following way:

<table>
    <tr>
        <td><code>+</code></td>
        <td>Uncommitted changes in the index</td>
    </tr>
    <tr>
        <td><code>!</code></td>
        <td>Unstaged changes</td>
    </tr>
    <tr>
        <td><code>?</code></td>
        <td>Untracked files</td>
    </tr>
    <tr>
        <td><code>$</code></td>
        <td>Stashed files</td>
    </tr>
</table>

Further details are in the `bash_prompt` file.

Screenshot:

![](http://i.imgur.com/MofvX7M.png)
