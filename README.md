# OverTheWire Bandit: Complete Learning Journey

> A comprehensive walkthrough and reference guide for completing all 26 levels of the [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) challenge, progressing from absolute beginner to intermediate Linux command-line skills.

---

## 📚 About This Repository

This repository documents a complete progression through the **OverTheWire Bandit** wargame—a series of challenges designed to teach fundamental Linux/Unix command-line skills through hands-on hacking practice.

### What is OverTheWire Bandit?

Bandit is an interactive learning platform where each level requires you to:
- Find a hidden password or key
- Use command-line tools to locate, decode, or extract information
- SSH into the next level using the discovered credentials
- Progress through increasingly difficult challenges

### Who Should Use This?

- **Beginners** learning Linux command-line fundamentals
- **Cybersecurity students** building foundational hacking skills
- **DevOps engineers** refreshing command-line proficiency
- **Anyone** interested in security and penetration testing basics

---

## 🎯 Learning Objectives

By completing Bandit, you will master:

| Skill | Levels Covered |
|-------|-----------------|
| **Basic Commands** | `ls`, `cat`, `find`, `file` | 0–5 |
| **Text Processing** | `grep`, `sort`, `uniq`, `tr` | 6–10 |
| **Advanced Filtering** | `sed`, `awk`, `base64`, encoding | 11–15 |
| **SSH & Cryptography** | SSH keys, asymmetric encryption | 16–20 |
| **Scripting & Automation** | Cron jobs, bash scripting, system tasks | 21–26 |

---

## 🗂️ Repository Structure

```
OverTheWire-Bandit/
├── README.md                    # This file
├── CHALLENGES.md                # Level-by-level challenge descriptions
├── SOLUTIONS.md                 # Detailed solutions & explanations
├── /solutions/                  # Organized solution guides
│   ├── LEVEL_00_TO_05.md       # Basic commands
│   ├── LEVEL_06_TO_10.md       # Text processing
│   ├── LEVEL_11_TO_15.md       # Advanced filtering
│   ├── LEVEL_16_TO_20.md       # SSH & cryptography
│   └── LEVEL_21_TO_26.md       # Scripting & automation
├── /credentials/                # Password/key reference
│   ├── passwords.txt            # Text-based passwords
│   └── ssh-keys/                # Private SSH keys
└── NOTES.md                     # Useful commands & tips reference
```

---

## 🚀 Quick Start

### Prerequisites

- SSH client installed (`ssh` on macOS/Linux, PuTTY on Windows)
- Terminal/command-line comfort (will build throughout!)
- ~2–3 hours for the complete challenge

### Getting Started

1. **Visit the official challenge**: https://overthewire.org/wargames/bandit/
2. **Start at Level 0**: Read the objective and attempt to solve it yourself
3. **Get stuck?** Check the relevant solution file in `/solutions/`
4. **SSH into your next level** once you've found the password

### Basic SSH Command

```bash
ssh bandit<level>@bandit.labs.overthewire.org -p 2220
# Password: [found from previous level]
```

---

## 📖 Level Progression

### **Beginner (Levels 0–5): Command Basics**
Essential tools: `ls`, `cat`, `cd`, `file`, `find`

### **Intermediate (Levels 6–10): Text Filtering**
Tools: `grep`, `sort`, `uniq`, `strings`, `wc`

### **Advanced (Levels 11–15): Data Encoding & Manipulation**
Tools: `base64`, `xxd`, `tr`, command chaining

### **Expert (Levels 16–20): SSH & Cryptography**
Concepts: RSA keys, port forwarding, SSL/TLS connections

### **Master (Levels 21–26): System Administration & Scripting**
Tools: cron, bash scripting, process management, environment exploitation

---

## 🔍 How to Use This Repository

### For Self-Study
1. Read the challenge objective from the official site
2. Attempt it yourself (15–30 minutes)
3. If stuck, review the **hint** section in `SOLUTIONS.md`
4. Only then, read the full solution
5. Verify the credentials in `/credentials/`

### For Reference
- Use `NOTES.md` for quick command syntax
- Check the solutions index for specific techniques
- Use the SSH keys folder as a last resort

### For Teaching
- Share specific level solutions to explain concepts
- Use the progression structure to scaffold learning
- Reference the objectives table for skill-building paths

---

## 📝 Solution Files

Each solution includes:

```
### Level X → Level X+1: [Challenge Name]

**Objective**: [What you need to find]

**Key Concepts**: 
- Concept 1
- Concept 2

**Hints** (try these before reading the solution):
1. Hint 1
2. Hint 2

**Solution**:
$ [command]
Result: [output]

**Explanation**: 
[Why this works]

**Password for Level X+1**: `xxxxxxxxxxxx`
```

---

## 🛠️ Useful Commands Reference

### Essential File Commands
```bash
ls -la              # List all files with details
cat filename        # Display file contents
file filename       # Identify file type
find . -name "*.txt"  # Search for files
strings binary      # Extract text from binary files
```

### Text Processing
```bash
grep "pattern" file      # Search for text
sort file                # Sort lines
uniq file                # Remove duplicates
wc -l file               # Count lines
sed 's/old/new/' file    # Replace text
awk '{print $1}' file    # Extract columns
```

### Encoding & Decoding
```bash
base64 -d file           # Decode base64
xxd -r file              # Reverse hex dump
tr '[a-z]' '[A-Z]'       # Translate characters
```

---

## 🎓 Learning Tips

1. **Don't Rush**: Spend time understanding each command
2. **Experiment**: Try variations of commands in a safe environment
3. **Google Is Your Friend**: Learn to search for command syntax
4. **Read Man Pages**: `man grep` teaches you more than any guide
5. **Take Notes**: Document what you learned at each level

---

## 🔒 Security & Ethics

⚠️ **This is for Educational Purposes Only**

- The Bandit challenge is **explicitly designed for learning**
- These credentials are part of a public wargame (not real systems)
- Apply these skills ethically and legally
- Never use these techniques on systems without permission

---

## 📚 Additional Resources

- **Official Bandit**: https://overthewire.org/wargames/bandit/
- **Linux Command Cheat Sheet**: https://cheatography.com/davechild/cheat-sheets/linux-command-line/
- **Bash Scripting Guide**: https://www.gnu.org/software/bash/manual/
- **SSH Best Practices**: https://linux.die.net/man/1/ssh
- **Regex Tester**: https://regex101.com/

---

## 🤝 Contributing

Have a better solution? Found an error? Feel free to:
- Open an issue for clarifications
- Submit improvements to explanations
- Share alternative approaches

---

## 📄 License

This is a learning resource compiled for educational purposes. Respect the original OverTheWire project and platform.

---

## 💡 Next Steps After Bandit

Completed all 26 levels? Continue your learning journey:

- **[Natas](https://overthewire.org/wargames/natas/)** - Web application security
- **[Leviathan](https://overthewire.org/wargames/leviathan/)** - Programming concepts
- **[Krypton](https://overthewire.org/wargames/krypton/)** - Cryptography basics
- **[CTF Competitions](https://ctftime.org/)** - Real-world hacking challenges

---

**Happy Hacking! 🎯**

> *"The only way to learn a new programming language is by writing programs in it." — Dennis Ritchie*

> *Same applies to command-line mastery: practice, practice, practice.*
