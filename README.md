# Mercurial plugin

extracted from oh-my-zsh, this is the original README

### Usage
Update .zshrc:

1. Add name to the list of plugins, e.g. `plugins = (..., mercurial, ...)`
   (that is pretty obvious).
2. Change PROMPT variable of current theme to contain current folder mercurial repo info:

   robbyrussel theme is used by default, so you need to modify PROMPT var
   from [this file](https://github.com/robbyrussell/oh-my-zsh/blob/master/themes/robbyrussell.zsh-theme)
   by adding `$(hg_prompt_info)` after `$(git_prompt_info)`, so currently it
   looks next:

   ```diff
   - PROMPT='${ret_status}%{$fg_bold[green]%}%p %{$fg[cyan]%}%c %{$fg_bold[blue]%}$(git_prompt_info)%{$fg_bold[blue]%} % %{$reset_color%}'
   + PROMPT='${ret_status}%{$fg_bold[green]%}%p %{$fg[cyan]%}%c %{$fg_bold[blue]%}$(git_prompt_info)$(hg_prompt_info)%{$fg_bold[blue]%} % %{$reset_color%}'
   ```
   
   and put modified var at the end of **.zshrc**.
3. Initialize additional vars used in plugin. So in short put next in **.zshrc**:
   
   ```
   ZSH_THEME_HG_PROMPT_PREFIX="%{$fg_bold[magenta]%}hg:(%{$fg[red]%}"
   ZSH_THEME_HG_PROMPT_SUFFIX="%{$reset_color%}"
   ZSH_THEME_HG_PROMPT_DIRTY="%{$fg[magenta]%}) %{$fg[yellow]%}✗%{$reset_color%}"
   ZSH_THEME_HG_PROMPT_CLEAN="%{$fg[magenta]%})"
   ```

### What's inside?
#### Adds handy aliases:
###### general
* `hgc` - `hg commit`
* `hgb` - `hg branch`
* `hgba` - `hg branches`
* `hgbk` - `hg bookmarks`
* `hgco` - `hg checkout`
* `hgd`  - `hg diff`
* `hged` - `hg diffmerge`

###### pull and update
* `hgi` - `hg incoming`
* `hgl` - `hg pull -u`
* `hglr` - `hg pull --rebase`
* `hgo` - `hg outgoing`
* `hgp` - `hg push`
* `hgs` - `hg status`
* `hgsl` - `hg log --limit 20 --template "{node|short} | {date|isodatesec} | {author|user}: {desc|strip|firstline}\n"`

###### this is the 'git commit --amend' equivalent
* `hgca` - `hg qimport -r tip ; hg qrefresh -e ; hg qfinish tip`

###### list unresolved files (since hg does not list unmerged files in the status command)
* `hgun` - `hg resolve --list`

#### Displays repo branch and directory status in prompt
This is the same as git plugin does.

**Note**: additional changes to **.zshrc** are required in order for this to
work.

### Mantainers
[ptrv](https://github.com/ptrv) - original creator

[oshybystyi](https://github.com/oshybystyi) - created this README and know how most of code works
