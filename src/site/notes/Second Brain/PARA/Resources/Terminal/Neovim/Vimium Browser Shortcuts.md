---
{"dg-publish":true,"dg-path":"Resources/Terminal/Neovim/Vimium Browser Shortcuts.md","permalink":"/resources/terminal/neovim/vimium-browser-shortcuts/","created":"2024-09-01T14:28:32.440-07:00","updated":"2024-09-01T14:28:32.440-07:00"}
---

>[!info] 
> I just added this note because I am using vimium on my personal browser and my work browser. You can also use `?`  while the extension is active, and you can get a cheatsheet popup of your shortcuts.


- @ This information is generated and formatted with ChatGPT, using information from the documentation of Vimium.
## The Hacker's Browser

**Vimium** provides keyboard shortcuts for navigation and control in the spirit of Vim.

**NOTE:** Google does not allow Vimium to run on this Chrome Web Store page and the Chrome New Tab page, by design. Sorry about that!

**NOTE:** Chrome has some alarmist messaging around the permissions that Vimium needs to run. Really, all it's asking for is that Vimium's JavaScript be loaded into every page. Don’t be alarmed. Vimium never talks to any servers and does absolutely nothing with your data. [Read the open source code](https://github.com/philc/vimium/blob/master/README.md) if you're curious.

For more information about rebinding your keys and how to use many of Vimium's features, see the [Vimium README](https://github.com/philc/vimium/blob/master/README.md).

Modifier keys are specified as `<c-x>`, `<m-x>`, `<a-x>` for `ctrl+x`, `meta+x`, and `alt+x` respectively.

### Navigating the Current Page

> `?` is going to be the best way to see a cheatsheet but having this on hand could be good for a reference outside of the browser...

- ! `?` - Show the help dialog for a list of all available keys
- `h` - Scroll left
- `j` - Scroll down
- `k` - Scroll up
- `l` - Scroll right
- `gg` - Scroll to the top of the page
- `G` - Scroll to the bottom of the page
- `d` - Scroll down half a page
- `u` - Scroll up half a page
- `f` - Open a link in the current tab
- `F` - Open a link in a new tab
- `r` - Reload
- `gs` - View source
- `i` - Enter insert mode — all commands will be ignored until you hit `esc` to exit
- `yy` - Copy the current URL to the clipboard
- `yf` - Copy a link URL to the clipboard
- `gf` - Cycle forward to the next frame

### Navigating to New Pages

- `o` - Open URL, bookmark, or history entry
- `O` - Open URL, bookmark, or history entry in a new tab
- `b` - Open bookmark
- `B` - Open bookmark in a new tab

### Using Find

- `/` - Enter find mode — type your search query and hit `enter` to search or `esc` to cancel
- `n` - Cycle forward to the next find match
- `N` - Cycle backward to the previous find match

### Navigating Your History

- `H` - Go back in history
- `L` - Go forward in history

### Manipulating Tabs

- `J`, `gT` - Go one tab left
- `K`, `gt` - Go one tab right
- `g0` - Go to the first tab
- `g$` - Go to the last tab
- `t` - Create tab
- `x` - Close current tab
- `X` - Restore closed tab (i.e., unwind the 'x' command)
- `T` - Search through your open tabs

### Additional Advanced Browsing Commands

- `]]` - Follow the link labeled 'next' or '>'. Helpful for browsing paginated sites.
- `[[` - Follow the link labeled 'previous' or '<'. Helpful for browsing paginated sites.
- `<a-f>` - Open multiple links in a new tab
- `gi` - Focus the first (or n-th) text input box on the page
- `gu` - Go up one level in the URL hierarchy

Vimium supports command repetition, so, for example, hitting `5t` will open 5 tabs in rapid succession. `ESC` (or `<c-[>`) will clear any partial commands in the queue and will also exit insert and find modes.

For release notes, see [Vimium's GitHub](https://github.com/philc/vimium).