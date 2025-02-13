# WindTerm
A whole new generation Telnet/SSH client.

_Hello WindTerm :rose:, hello world!_

**We're just beginning!**

# Roadmap

**Release cycle:**

  4-6 weeks.

**Next release (for reference only):**
- Fix bugs, make windterm stable enough for daily use.
- Session Manager.
- Reflow text when resized.
- Support IME.
- Timestamp.
- Connection status report.

**Todo list:**
- Protocols:
  - Serial
  - Rlogin
- SSH:
  - Auto login
  - Authentication: public-key, gssapi-with-mic
  - X11 forwarding
  - Port forwarding (Tunnel)
- UI:
  - Session dialog
  - Config dialog
- Terminal:
  - Auto complete
  - Cmd, powershell, wsl
  - Linux bash
  - MacOs bash
- Session:
  - Keep alive
  - Proxy
  - Chat mode
  - Log and log viewer
- File transfer:
  - Integrate ftp, sftp, scp client
  - Xmodem, Ymodem, Zmodem
  - sz, rz
- Script, macro and plugin stystem
- More ...

# Issues and feature requests

Any issues and feature requests are welcome. Please click [issues](https://github.com/kingToolbox/WindTerm/issues) to commit an issue.

# Download

Windows Binary: https://github.com/kingToolbox/WindTerm/releases

(The binary of Macos and Linux will be committed later)

# Screenshots

WSL:

![WSL](https://github.com/kingToolbox/WindTerm/blob/master/images/screenshots/WSL.png)

Split views:

![SplitView](https://github.com/kingToolbox/WindTerm/blob/master/images/screenshots/SplitView.png)


# Features
- Telnet and SSH v2 protocols implemented.
- Support vt100, vt220, vt340, vt420, vt520, xterm, xterm-256-colors.
- Support color schemes like vscode.
- Support folding, outlining, split views.
- Support unicode, true-color, mouse protocol, etc.
- Support searching and previewing.
- Restore last sessions and layouts when restart. 
- Protocols and terms can be customed.
- All vttest tests have passed except Tektronix 4014.
- High performance, low memory, low latency.

# Shortcuts

| Shortcut | Action |
| --- | --- |
| Alt+C | Copy |
| Alt+D | Show command palette |
| Alt+F | Find |
| Alt+F3 | Find next |
| Alt+Shift+F3 | Find previous |
| Alt+F4 | Exit |
| Alt+M, Alt+F | Toggle full screen |
| Alt+M, Alt+H | Toggle hex view |
| Alt+N | New session |
| Alt+O | Open session |
| Alt+S | Save text |
| Alt+T, Alt+B | Toggle margin blank |
| Alt+T, Alt+F | Toggle margin fold |
| Alt+T, Alt+N | Toggle margin number |
| Alt+T, Alt+S | Toggle margin symbol |
| Alt+V | Paste |
| Alt+W, Alt+D | Close active dock |
| Alt+W, Alt+G | Close active group |
| Alt+W, Alt+H | Split horizontally |
| Alt+W, Alt+L | Show outline pane |
| Alt+W, Alt+V | Split vertically |
| Alt+X | Copy and paste |
| Alt+- | Zoom in |
| Alt++ | Zoom out |
| Alt+\[ | Activate next view |
| Alt+] | Activate previous view |
| Ctrl+. | Jump to next fold |
| Ctrl+, | Jump to previous fold |
| Ctrl+Shift+A | Select all text |
| Ctrl+Shift+T | Reopen closed session |
| Ctrl+Shift+W | Close current session |
| Ctrl+Shift+- | Select current fold text |
| Shift+Del | Copy |
| Shift+End | Jump to document end |
| Shift+Home | Jump to document home |
| Shift+Ins | Paste |
| Shift+PgDown | Jump to next page |
| Shift+PgUp | Jump to previous page |

# Performance

The hardware used for generating the data in these benchmarks was

    windows 10 - 2.3 GHz Intel Core i5 and 8GB memory.
    MacOs 10.13 - 2.3 GHz Intel Core i5 and 8GB memory.

**WindTerm, rxvt, putty, xterm** tests are performed on WSL(Ubuntu 18.04.2). 

**Iterm2, kitty, Alacritty** tests are performed on MacOS shell, 

    For WindTerm: No color scheme used in windterm. Color scheme will result in approximately 2% loss and more memory usage.

    For Alacritty: Can not find how to set the scrollback lines limit, so every test use its default setting and no memory usage measured.

The version of terminals:

    windterm      v0.8
    rxvt-unicode: v9.2.2
    putty:        v0.71
    xterm:        v3.30
    iterm2:       v3.3.6
    alacritty:    v0.3.3
    kitty:        v0.14.6

**All test data is for reference only.**

- 97.6MB random text (102,401,504 bytes, 1,329,878 lines, generated and tested by [random_test.sh](https://github.com/kingToolbox/WindTerm/blob/master/benchmark/urandom_test.sh))

In all cases, three runs were made to warm system caches. The reported numbers are the median of five runs. 

1. Telnet:

| | Lines of scrollback | Data Rate(MB/sec) | Memory Usage(MB) |
| --- | --- | --- | --- |
| WindTerm | unlimited | **51.6** | **98.5** |
| rxvt | 1,350,000 | 37.8 | 842.2 | 
| Putty | 1,350,000 | 4.9 | 733.4 |
| xterm | 1,350,000 | 2.2 | 3328.4 |

2. SSH:

| | Lines of scrollback | Data Rate(MB/sec) | Memory Usage(MB) |
| --- | --- | --- | --- |
| WindTerm | unlimited | **50.5** | **98.1** |
| rxvt | 1,350,000 | 40.2 | 842.2 | 
| Putty | 1,350,000 | 4.8 | 734.9 |
| xterm | 1,350,000 | 2.3 | 3328.4 |

3. Shell:

| | Lines of scrollback | Data Rate(MB/sec) | Memory Usage(MB) |
| --- | --- | --- | --- |
| iterm2 | unlimited | - (Take too long time) | more than 1300 |
| kitty | unlimited | 17.2 | 2655 |
| Alacritty | Limited scrollback | 41.4 | - |

- time seq 1 n

1. n = 1,000,000, scrollback = 1,000,000 Lines

| | Time(sec) | Memory Usage(MB) |
| --- | --- | --- |
| WindTerm | **1.141** | **10.6** |
| rxvt | 5.082 | 633.3 |
| putty | 4.161 | 551.1 |
| xterm | 40.421 | 2500.7 |
| iterm2 | 2.116 | 146.3 |
| Kitty | 2.535 | 2376.5 |
| Alacritty | 1.215 | Not measured, use its default scrollback setting |

2. n = 2,000,000, scrollback = 2,000,000 Lines

| | Time(sec) | Memory Usage(MB) |
| --- | --- | --- |
| WindTerm | **2.053** | **16.0** |
| rxvt | 10.896 | 1266.6 |
| putty | 16.045 | 1102.6 |
| xterm | 68.154 | 5005.5 |
| iterm2 | 4.181 | 383.2 |
| Kitty | 5.620 | 4749.9 |
| Alacritty | 2.448 | Not measured, use its default scrollback setting |

3. n = 5,000,000 scrollback = 5,000,000 Lines

| | Time(sec) | Memory Usage(MB) |
| --- | --- | --- |
| WindTerm | **4.839** | **38.7** |
| rxvt | 27.533 | 3166.2 |
| putty | 45.911 | 2757.1 |
| xterm | - | Out of memmory |
| iterm2 | 10.805 | 1048.3 |
| Kitty | - | Out of memory |
| Alacritty | 6.172 | Not measured, use its default scrollback setting |

4. n = 10,000,000 scrollback = 10,000,000 Lines

| | Time(sec) | Memory Usage(MB) |
| --- | --- | --- |
| WindTerm | **9.576** | **78.6** |
| rxvt | - | Out of memory |
| putty | - | Out of memory |
| xterm | - | Out of memmory |
| iterm2 | 20.468 | 2231.3 |
| Kitty | - | Out of memory |
| Alacritty | 12.332 | Not measured, use its default scrollback setting |

5. n = 10,000,000 scrollback = 30 Lines

| | Time(sec) | Memory Usage(MB) |
| --- | --- | --- |
| WindTerm | **9.514** | 2.2 |
| rxvt | 9.687 | **0.1** |
| putty | 95.382 | 0.4 |
| xterm | 286.510 | **0.1** |
| iterm2 | 25.448 | 7.4 |
| Kitty | 16.104 | 0.5 |
| Alacritty | 12.221 | Not measured, use its default scrollback setting |

# Latency

Considering the network influence on the latency, the following data is from [DIGEdit](https://github.com/kingToolbox/digedit).
DIGEdit is the text component of WindTerm.

|   | Min | Max | Avg | SD |
| --- | --- | --- | --- | --- |
|DIGEdit| 1.9 | 7.6 | 2.9 | 0.8 |
|Windows Notepad | 0.9 | 16.5 | 7.8 | 1.8 |
|GVim | 0.9 | 10.4 | 2.8 | 1.2 |

# License
Free for personal use. Currently limited to a maximum of 16 sessions.
