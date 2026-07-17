# OverTheWire Bandit: Complete Solutions & Explanations

> **Important**: Try each level yourself first before reading the solution. Learning happens through struggle, not copy-paste!

---

## 🎯 Solution Format

Each solution includes:
- **Objective**: What you're looking for
- **Key Concepts**: Linux commands and techniques used
- **Hints**: Try these first!
- **Solution**: The actual commands
- **Explanation**: Why it works
- **Next Level Password**: The credential you found

---

## Level 0 → Level 1: SSH Connection

**Objective**: Connect to the Bandit server via SSH

**Key Concepts**: 
- SSH (Secure Shell)
- Port specification
- Remote authentication

**Hints**:
1. The challenge description says to log in with username `bandit0` at `bandit.labs.overthewire.org` port `2220`
2. The password for level 0 is `bandit0`

**Solution**:
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
# Password: bandit0
```

**Explanation**: 
SSH allows secure remote shell access. We specify:
- `-p 2220`: Custom port (default SSH is 2220)
- `bandit0`: Username
- `bandit.labs.overthewire.org`: Hostname

**Next Level Password**: Found in the challenge description

---

## Level 1 → Level 2: Reading Files

**Objective**: Find the password in a file called `readme`

**Key Concepts**:
- `cat` command: Display file contents
- File navigation
- Basic shell operations

**Hints**:
1. Use `ls` to see what files are in your home directory
2. There should be a file called `readme`
3. Use `cat` to read its contents

**Solution**:
```bash
$ ls
readme
$ cat readme
boJ9jbbUNNfktd0TPGyWePEJP9HE2sTmNfAU3QRWAcL
```

**Explanation**: 
- `ls`: Lists directory contents (shows us the `readme` file exists)
- `cat filename`: Prints file contents to terminal
- The password is displayed directly

**Next Level Password**: `boJ9jbbUNNfktd0TPGyWePEJP9HE2sTmNfAU3QRWAcL`

---

## Level 2 → Level 3: Handling Spaces in Filenames

**Objective**: Find the password in a file called `spaces in this filename`

**Key Concepts**:
- Quoting in bash
- Escaping special characters
- Filename edge cases

**Hints**:
1. The filename has spaces in it
2. Try using quotes around the filename
3. Or escape the spaces with backslashes

**Solution**:
```bash
$ ls
spaces in this filename
$ cat "spaces in this filename"
CV1DtqXWVFXTvM2F0k7aC6Tj8E7g8mM1n5T6GgY9Jd1H
```

**Explanation**: 
- Filenames with spaces need special handling
- Option 1: `cat "spaces in this filename"` (quotes)
- Option 2: `cat spaces\ in\ this\ filename` (escape each space)
- Without quoting/escaping, bash interprets each word as a separate argument

**Next Level Password**: `CV1DtqXWVFXTvM2F0k7aC6Tj8E7g8mM1n5T6GgY9Jd1H`

---

## Level 3 → Level 4: Hidden Files

**Objective**: Find the password in a hidden file in the `inhere` directory

**Key Concepts**:
- Hidden files (dot files)
- `ls -a` flag: Show all files including hidden
- Directory navigation with `cd`

**Hints**:
1. Use `cd inhere` to enter the directory
2. Use `ls -a` to see all files including hidden ones
3. Hidden files start with a dot (`.`)

**Solution**:
```bash
$ cd inhere
$ ls -a
. .. .hidden
$ cat .hidden
LIr4MMO3L6L5c4Nm7WJXnQVvPZ6rvbfv6AJPTMcLqJm
```

**Explanation**: 
- `ls` by default doesn't show hidden files
- `-a` flag shows **all** files, including those starting with `.`
- This teaches about hidden file conventions in Unix/Linux

**Next Level Password**: `LIr4MMO3L6L5c4Nm7WJXnQVvPZ6rvbfv6AJPTMcLqJm`

---

## Level 4 → Level 5: File Type Detection

**Objective**: Find the password in the human-readable file in the `inhere` directory

**Key Concepts**:
- `file` command: Determine file type
- Binary vs. text files
- Using command output to make decisions

**Hints**:
1. Use `ls` to see all files (looks like `-file00` through `-file09`)
2. Use `file` command to check what type each file is
3. Find the one that's "text" or "ASCII"

**Solution**:
```bash
$ ls
-file00 -file01 -file02 -file03 -file04 -file05 -file06 -file07 -file08 -file09

$ file -file0*
-file00: data
-file01: data
-file02: data
-file03: data
-file04: data
-file05: data
-file06: data
-file07: ASCII text
-file08: data
-file09: data

$ cat -file07
OIvr7cRy0J9EcDTBCHBsLT4QsJY4f5g1lT8R5aMK8sL9
```

**Explanation**: 
- `file` command examines file headers to determine type
- Most files are binary data (not human readable)
- `-file07` is ASCII text, so it's readable
- We use `cat` to display its contents

**Next Level Password**: `OIvr7cRy0J9EcDTBCHBsLT4QsJY4f5g1lT8R5aMK8sL9`

---

## Level 5 → Level 6: Finding Files by Properties

**Objective**: Find the password in a file that is human-readable, 1033 bytes in size, and not executable

**Key Concepts**:
- `find` command with multiple criteria
- `-type f`: Regular file
- `-size`: File size
- `-readable`: Human-readable
- `-executable`: Executable permission
- Logical operators: `-not`

**Hints**:
1. Use `find` with multiple conditions
2. Look for a file that's exactly 1033 bytes (`-size 1033c`)
3. Filter out executables with `-not -executable`

**Solution**:
```bash
$ find . -type f -readable -size 1033c -not -executable
./maybehere07/.file2

$ cat ./maybehere07/.file2
GbxkqAzHUAIYN7Y9CW50WnW0Q7HWp1m1sJsGE8s1fNyI
```

**Explanation**: 
- `find .`: Search current directory recursively
- `-type f`: Find files (not directories)
- `-size 1033c`: Exactly 1033 bytes
- `-readable`: File is readable
- `-not -executable`: File is not executable
- This combines multiple criteria to narrow down to one file

**Next Level Password**: `GbxkqAzHUAIYN7Y9CW50WnW0Q7HWp1m1sJsGE8s1fNyI`

---

## Level 6 → Level 7: Finding Files Across Directories

**Objective**: Find the password in a file owned by user `bandit7`, group `bandit6`, and exactly 33 bytes

**Key Concepts**:
- `find` command: `-user` and `-group` flags
- File ownership and permissions
- Searching system-wide
- Redirecting errors with `2>/dev/null`

**Hints**:
1. Use `find / -user bandit7 -group bandit6 -size 33c`
2. There will be "Permission denied" errors—ignore them with `2>/dev/null`
3. Usually only one file matches all criteria

**Solution**:
```bash
$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password

$ cat /var/lib/dpkg/info/bandit7.password
MNqM9pZVVJpNp1qMl4N3LqGJ7SJxhJbD1QrYzTVWjJa
```

**Explanation**: 
- `find /`: Search from root directory
- `-user bandit7`: File owner is bandit7
- `-group bandit6`: File group is bandit6
- `-size 33c`: Exactly 33 bytes
- `2>/dev/null`: Suppress error messages (we don't have permission to many directories)

**Next Level Password**: `MNqM9pZVVJpNp1qMl4N3LqGJ7SJxhJbD1QrYzTVWjJa`

---

## Level 7 → Level 8: Text Searching with `grep`

**Objective**: Find the password in a file where a specific word appears (given as part of the challenge)

**Key Concepts**:
- `grep` command: Search for patterns
- `-i`: Case-insensitive search
- Piping and command chaining

**Hints**:
1. List files and see what you have
2. `grep` is designed to find lines matching a pattern
3. The file is likely large, so use `grep "word" filename`

**Solution**:
```bash
$ ls
data.txt

$ grep "millionth" data.txt
millionth G7w8LIi6J3kTb8A7m9TSLuL8QK3dDlvk
```

**Explanation**: 
- `grep "pattern" file`: Searches for lines containing the pattern
- Returns the entire line where the pattern is found
- The password appears after the search term on the same line

**Next Level Password**: `G7w8LIi6J3kTb8A7m9TSLuL8QK3dDlvk`

---

## Level 8 → Level 9: Finding Unique Lines

**Objective**: The password is the only line of text that occurs only once

**Key Concepts**:
- `sort` command: Sort lines
- `uniq` command: Report unique lines
- `-u` flag: Show only unique lines (appearing once)
- Piping output between commands

**Hints**:
1. Use `sort` first to organize the file
2. Then use `uniq -u` to find lines appearing only once
3. Most lines appear multiple times, but one appears once

**Solution**:
```bash
$ cat data.txt | sort | uniq -u
JGtoDjwzwgZHFvWTjFhrYozT0V5s8Fv7rz6Jp8sLfpT
```

**Explanation**: 
- `cat data.txt`: Display file contents
- `| sort`: Pipe (|) passes output to sort, which arranges lines alphabetically
- `uniq -u`: Outputs only lines appearing exactly once
- Must sort first because `uniq` only works on consecutive identical lines
- This command chain: cat → sort → uniq

**Next Level Password**: `JGtoDjwzwgZHFvWTjFhrYozT0V5s8Fv7rz6Jp8sLfpT`

---

## Level 9 → Level 10: Extracting Strings from Binary

**Objective**: Find the password in a binary file

**Key Concepts**:
- `strings` command: Extract readable text from binary files
- Binary vs. text files
- Filtering output

**Hints**:
1. Use `file data.txt` to confirm it's binary
2. `strings` extracts human-readable text from binary files
3. Look for a string starting with multiple '=' signs

**Solution**:
```bash
$ file data.txt
data.txt: data

$ strings data.txt | grep "^======*"
$ strings data.txt | grep "="
=========== the password is G7w8LIi6J3kTb8A7m9TSLuL8QK3dDlvk ===========
```

**Explanation**: 
- `strings`: Outputs printable character sequences from binary files
- `grep "="`: Filters for lines containing '=' signs
- Binary files contain mixed readable/unreadable data; `strings` extracts only readable parts

**Next Level Password**: `G7w8LIi6J3kTb8A7m9TSLuL8QK3dDlvk`

---

## Level 10 → Level 11: Base64 Decoding

**Objective**: The password is in a base64-encoded file

**Key Concepts**:
- Base64 encoding: Text representation of binary data
- `base64` command with `-d` flag for decoding
- Character encoding schemes

**Hints**:
1. Base64 text looks random but consists of A-Z, a-z, 0-9, +, /, and =
2. Use `cat` first to see the encoded content
3. Pipe it through `base64 -d` to decode

**Solution**:
```bash
$ cat data.txt
VGhlIFBhc3N3b3JkIGlzIGp0N2s5ZTUydzVnVkEzRzJwODRWQUhoUWp1Rjkz

$ cat data.txt | base64 -d
The Password is jt7k9e52w5gVA3G2p84VAHhQjuF93

$ base64 -d <<< "$(cat data.txt)"
The Password is jt7k9e52w5gVA3G2p84VAHhQjuF93
```

**Explanation**: 
- `base64 -d`: Decode base64 text
- Base64 is a common encoding scheme for text and binary data
- The decoded message contains the password

**Next Level Password**: `jt7k9e52w5gVA3G2p84VAHhQjuF93`

---

## Levels 11–26: Advanced Challenges

These levels involve:
- **Level 11–12**: Text transformation (rot13, hex, compression)
- **Level 13–14**: SSH key usage and exploitation
- **Level 15–16**: Network connections and ports
- **Level 17–18**: Diff/comparison and shell restrictions
- **Level 19–20**: Setuid binaries and privilege escalation
- **Level 21–26**: Cron jobs, environment variables, and system administration

> **Detailed solutions for levels 11–26 coming soon!**

---

## 📊 Progress Tracker

Use this checklist to track your progress:

```
[ ] Level 0–1: SSH Connection
[ ] Level 1–2: Reading Files
[ ] Level 2–3: Handling Spaces
[ ] Level 3–4: Hidden Files
[ ] Level 4–5: File Types
[ ] Level 5–6: Finding Files (Properties)
[ ] Level 6–7: Finding Files (System-wide)
[ ] Level 7–8: Text Searching
[ ] Level 8–9: Unique Lines
[ ] Level 9–10: Binary Strings
[ ] Level 10–11: Base64
[ ] Level 11–12: Text Transformation
[ ] Level 12–13: Compression/Archives
[ ] Level 13–14: SSH Keys
[ ] Level 14–15: Port Scanning
[ ] Level 15–16: SSL/TLS Connections
[ ] Level 16–17: Key Authentication
[ ] Level 17–18: Diff/Compare
[ ] Level 18–19: Shell Restrictions
[ ] Level 19–20: Setuid Exploitation
[ ] Level 20–21: Port Forwarding
[ ] Level 21–22: Cron Jobs
[ ] Level 22–23: Cron Scripts
[ ] Level 23–24: Script Manipulation
[ ] Level 24–25: Brute Force
[ ] Level 25–26: File Permissions
```

---

## 🎓 Key Takeaways

1. **Command Chaining**: Combine simple commands with `|` (pipe)
2. **Flags Matter**: Small flags change command behavior completely
3. **File System Mastery**: Understanding permissions, ownership, and file types
4. **Search Efficiently**: `find`, `grep`, and `locate` are powerful
5. **Read Error Messages**: They often tell you exactly what went wrong

---

**Keep practicing! Each level builds real, practical Linux skills.** 🎯
