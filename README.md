# walk :hiking_boot:

**This fork:**

- Configures Walk for left-handed use
- Differences with upstream are signposted with a :warning:
- Feature parity is a non-goal

---

<p align="center">
  <br>
  <img src=".github/images/demo.gif" width="600" alt="walk demo">
  <br>
</p>

**Walk** — a terminal navigator.

Why another terminal navigator? I wanted something simple and minimalistic.
Something to help me with faster navigation in the filesystem; a cd and ls
replacement. So I build **walk**. It allows for quick navigation with fuzzy
searching, cd integration is quite simple. And you can open vim right from
the walk. That's it.

## Install :warning:

Use `go build` for now.

Then put this function into the **.bashrc** or a similar config:

Bash:

```bash
function lk {
  cd "$(walk "$@")"
}
```

Fish:

```fish
function lk
  set loc (walk $argv); and cd $loc;
end
```

Powershell:

```powershell
function lk() {
  cd $(walk $args)
}
```

Now use `lk` command to start walking.

### Preview mode

Press `,` to toggle preview mode.

<img src=".github/images/preview-mode.gif" width="600" alt="Walk Preview Mode">

### Delete file or directory

Press `delete` to delete file or directory. Press `u` to undo.

<img src=".github/images/rm-demo.gif" width="600" alt="Walk Deletes a File">

### Display icons

Install [Nerd Fonts](https://www.nerdfonts.com) and add --icons flag.

<img src=".github/images/demo-icons.gif" width="600" alt="Walk Icons Support">

### Image preview

No additional setup is required.

<img src=".github/images/images-mode.gif" width="600" alt="Walk Image Preview">

## Usage :warning:

```
 Key binding       Description
--------------------------------------
arrows, wasd, hjkl  Move cursor
shift+up, W, g      Move to top of column
shift+dn, D, G      Move to bottom of column
Home                Move to beginning
End                 Move to end
enter, space        Enter directory/Open file
backspace           Exit directory
esc, q              Exit with cd
ctrl+c              Exit without cd
,                   Toggle preview
.                   Hide hidden files
/, f                Fuzzy search
delete              Delete file or dir
y                   Yank current dir

```

**Note:** Files should open in their default programs. This uses
Invoke-Item on Windows or xdg-open on Linux. This is **very
experimental**.

## Configuration :warning:

The WALK_REMOVE_CMD environment variable can be used to specify a command to
be used to remove files. This is useful if you want to use a different
command to remove files than the default rm.

```bash
export WALK_REMOVE_CMD=trash
```

Flags can be used to change the default behavior of the program.

```
 Flag          Description
------------------------------------------
 --icons     Show icons
 --dir-only  Show dirs only
 --preview   Start with preview mode on
 --fuzzy     Start with fuzzy search on
```

## License

[MIT](LICENSE)
