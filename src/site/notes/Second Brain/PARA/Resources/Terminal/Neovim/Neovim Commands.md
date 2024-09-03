---
{"dg-publish":true,"dg-path":"Resources/Terminal/Neovim/Neovim Commands.md","permalink":"/resources/terminal/neovim/neovim-commands/","created":"2024-09-01T14:28:32.440-07:00","updated":"2024-09-01T14:28:32.440-07:00"}
---

Nvim-Treesitter

- if there are more treesitter errors from Nvim 

use this for a quick fix: `:TSUpdate` 

[Nvim Reference](https://github.com/nvim-treesitter/nvim-treesitter/issues/3092)

---


1. To fold a section of code, move the cursor to the desired line and enter the command mode again.

2. Type the following command to fold the code block containing the current line:
   ```
   zc
   ```

   The code block will collapse, and you will see a fold marker indicating the folded code.

3. To unfold a folded code block, move the cursor to the fold marker and enter the command mode.

4. Type the following command to unfold the code block:
   ```
   zo
   ```

   The code block will expand, and you will be able to see the folded code.

Additionally, you can use different commands and keybindings to navigate and manipulate code folding in Neovim. Here are a few useful ones:

- `zm`: Close all folds in the current buffer.
- `zr`: Open all folds in the current buffer.
- `za`: Toggle the folding state of the current fold.
- `zc`: Close the current fold.
- `zo`: Open the current fold.
- `zj`: Move the cursor to the next fold.
- `zk`: Move the cursor to the previous fold.

# VSCode Obsidian Vim Commands
---
### The "norm" command 

```vim
:<,>norm I- 
```

*norm* stands for "normal" (and can also be used as the command)

### Use Case

> Say that you wanted to add a " - " to the beginning of line 68 and 69
> Instead of doing it by hand, you can select the lines, enter **command mode** by hitting " : ", type "norm", and type out the normal mode steps you want to take, and then hit enter

**try it below 👍**

- hello
hello world
hello world

### Use Case

> add "this is a comment" to the ends of both lines with the **normal** command

```python
tacos = tacobar.request(2) # 
burritos = restaurant.request(1) #
```

>[!globe]- Solution
>norm AThis is a Comment


# Marks

Certainly! Marks in Neovim (and Vim) are a powerful feature that allow you to set "bookmarks" within your text and quickly jump to them later. Here's a comprehensive guide on how to use marks in Neovim:

1. Setting Marks:
   - To set a mark, type `m` followed by a character (a-z or A-Z).
   - Lowercase marks (a-z) are specific to a buffer.
   - Uppercase marks (A-Z) are global and can be used across buffers.

   Example: `ma` sets a mark named 'a' at the current cursor position.

2. Jumping to Marks:
   - To jump to a mark, use a backtick (`) followed by the mark character.
   - You can also use a single quote (') to jump to the beginning of the line containing the mark.

   Example: ``a` jumps to mark 'a', `'a` jumps to the start of the line containing mark 'a'.

3. Listing Marks:
   - Use `:marks` to list all marks.
   - Use `:marks abc` to list specific marks (a, b, and c in this case).

4. Deleting Marks:
   - Use `:delmarks` followed by the mark names to delete specific marks.
   - Use `:delmarks!` to delete all lowercase marks for the current buffer.

   Example: `:delmarks a` deletes mark 'a', `:delmarks!` deletes all lowercase marks.

5. Special Marks:
   Neovim has several special marks:
   - `'` : Position before the last jump within current file
   - `"` : Position when last exiting the current buffer
   - `[` : Start of the last change or yank
   - `]` : End of the last change or yank
   - `<` : Start of the last visual selection
   - `>` : End of the last visual selection

6. Using Marks with Commands:
   You can use marks with many Vim commands.
   
   Example: `d'a` deletes from the current line to the line containing mark 'a'.

7. Automatic Marks:
   Neovim automatically sets some marks:
   - `''` : Position before the last jump
   - ``.`` : Location of last change
   - `'^` : Location of last insertion
   - `'[` : Start of last change or yank
   - `']` : End of last change or yank

8. File Marks:
   When you exit Neovim, it saves the location of your cursor in the last 100 files you edited. When you reopen these files, you can jump to the last position with `'"`.

Here's a practical example of using marks:

1. Place your cursor where you want to set a mark and type `ma`.
2. Move around in your file.
3. To jump back to the mark, type ``a`.
4. To see all your current marks, type `:marks`.

Marks are particularly useful when you're working with large files or moving between different sections of code frequently. They provide a quick way to navigate without needing to search or scroll.

Remember, practice is key to becoming proficient with marks. Start by using them for simple navigation tasks, and gradually incorporate them into your regular workflow as you become more comfortable.

# Pipe command output into buffer

example:

```markdown
echo "hello world"
```

to run this command and then replace command with it's output:

1. select the text with visual mode
2. press ':' and then do "!zsh" or whatever shell you are using or what to send this command to.
3. the stdout of the command will then be inserted into the space that your visual selection was occupying.

>[!attention] "J"
>if you use `J` you can move the line under where your cursor is, to your current line


## Search and Replace

> [!anchor] Lets you search for something with pure text or regular expressions and then you can define what you want to replace or change about your search results.

### Example:

- Say you are trying to fix this statement: 

```python
def send_req_to_server(**kwargs):

    st.write(f'URL is {url}, and summary type is {summary_type}')
```

you want to convert the `st.write` method to have this instead:

`f'URL is {kwargs['url']}, and summary type is {kwargs['summary_type']}`

yes you could just do it for the first one, then copy, paste quickly and change it to be `summary_type`

This is Vim gosh darn it, we can do better than that.

so we can use the search and replace command and regex to do this :LiArrowDown:

```vim
:<,>s/{\(\w*\)}/{kwargs['\1']}/g
```

This works as follows:

- `:<,>` denotes that we visually selected the line we wanted to update (don't really have to worry about that)
- ! `s/__1__/__2__/g`
	- to break this down is simply:
		- `s` starts the search and replace command
		- whatever is in between the slashes (1) is going to be searched for
		- whatever you put in the second slot of slashes (2) is going to be what is replacing your search results
		- the `g` at the end helps vim know you want to do this globally within your selection
- `{\(\w*\)}`: The `{` and `}` are outside of the capture group `\(\w*\)`, *which only captures the word characters between the curly braces.*
- In the replacement, you reference the captured word with `\1`, which excludes the curly braces themselves, thus only capturing what’s inside the braces.

>[!attention] Watch Out...
>Make sure you escape `[ ]` in vim search and replace because it's a regex special character

