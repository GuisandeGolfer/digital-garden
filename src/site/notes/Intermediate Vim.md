---
{"dg-publish":true,"permalink":"/intermediate-vim/","noteIcon":"","updated":"2024-09-10T08:37:59.441-07:00"}
---


Notes from this article: [A Vim Guide for Intermediate Users](thevaluable.dev/vim-intermediate)

## Buffer Commands
---
To navigate through the buffer list, you can use these commands:

- `:buffer <ID_or_name>` - Move to the buffer using its ID or its name.
- `bnext` - `:bn` move to the next buffer
- `:bprevious` or `:bp` - move to the previous buffer
- `:bfirst` or `:bf` move to the first buffer
- `:blast` or `:bl` move to the last buffer
- `CTRL-^` - switch to the alternate buffer. it's indicated in your buffer list with the symbol: `#`
- `<ID>CTRL_^` switch to a specific buffer with ID `<ID>`. For Example, 75CTRL-^ would switch to the buffer with ID 75.

you can also apply a command to all buffers with 

```vim
:bufdo <command>
```

> I feel like this could be really helpful for formatting files or automating mundane things that you can't do outside of vim.   

## `:bufdo` examples
---
Here are some examples of useful commands you can run with `:bufdo` in Vim:

The `update` command in Vim is used to save the current buffer to disk, but only if it has been modified. It's a more efficient alternative to the write command when you're not sure if changes have been made.


1. Search and replace across all buffers:
```
:bufdo %s/oldtext/newtext/g | update
```

2. Save all modified buffers:
```
:bufdo update
```

3. Convert all buffers to Unix line endings:
```
:bufdo set ff=unix | update
```

4. Add a line to the end of all buffers:
```
:bufdo $put='// End of file' | update
```

5. Remove trailing whitespace from all buffers:
```
:bufdo %s/\s\+$//e | update
```

6. Execute a macro named 'a' on all buffers:
```
:bufdo execute "normal! @a" | update
```

7. Set all buffers to a specific file type:
```
:bufdo set filetype=python
```

8. Close all buffers except the current one:
```
:bufdo bdelete | edit # | bdelete #
```

As for Zsh commands, `:bufdo` is specific to Vim and not directly applicable to Zsh. However, you can use Vim's `:bufdo` to execute shell commands on multiple files. For example:

9. Run a shell command on all open buffers:
```
:bufdo !zsh -c 'echo "Processing %"'
```

10. Use `sed` on all open buffers:
```
:bufdo !sed -i 's/old/new/g' %
```
