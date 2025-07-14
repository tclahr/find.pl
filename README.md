
# find.pl - Powerful Perl-Based File Search Utility

**`find.pl`** is a lightweight, flexible, and powerful command-line utility written in Perl that replicates and extends the behavior of Unix's native `find` command. With support for symbolic link traversal, depth-limited search, advanced expression parsing, and file metadata inspection, it's ideal for power users, sysadmins, and developers needing fine-grained control over file discovery tasks.

## 📖 Overview

`find.pl` is a feature-rich file search tool for Unix-like systems built using Perl. It walks a directory hierarchy, evaluating logical expressions to locate files and directories based on their name, permissions, type, size, and other attributes. It supports a wide range of tests, actions, and logical operators, offering a familiar and powerful alternative to the native `find(1)` command.

## 🚀 Features

- 🔎 **Expression-based matching**: Combine filters like `-name`, `-mtime`, `-size`, and `-perm`.
- ⛓️ **Symbolic link traversal**: Use `-L` to follow symlinks.
- 📁 **Depth control**: Limit search with `-maxdepth`.
- ⚡ **Exec actions**: Run custom commands on matched files using `-exec`.
- 🧪 **Advanced tests**:
  - File age: `-atime`, `-mtime`, `-ctime`
  - Permissions: `-perm`
  - Ownership: `-nouser`, `-nogroup`
  - Type: `-type` (e.g. files, directories, symlinks)
- 📌 **Actions**:
  - Print to stdout: `-print`, `-print0`
  - Skip directories: `-prune`
  - File stats output: custom `stat_pl` helper

## ⚙️ Usage

```bash
perl find.pl [-L] [starting-point] [expression]
```

### Examples

**Find all `.log` files modified in the last 2 days:**

```bash
perl find.pl /var/log -name "*.log" -mtime -2 -print
```

**Find files over 10 MB and display their details:**

```bash
perl find.pl /data -size +10M -exec stat_pl {} \;
```

**List all empty directories:**

```bash
perl find.pl . -type d -empty -print
```

**Search case-insensitively for `.jpg` files under `Pictures`:**

```bash
perl find.pl ~/Pictures -iname "*.jpg" -print
```

**Avoid descending into `.git` directories:**

```bash
perl find.pl . -path "*.git*" -prune -o -print
```

## 🧰 Requirements

- **Perl** version 5.10 or later
- Compatible with Unix-like environments (Linux, macOS, BSD)
- No external dependencies (pure Perl)

## 📜 License

This project is licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

## 🤝 Contributing

Contributions are welcome!

1. Fork this repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Make your changes and test thoroughly
4. Commit and push: `git commit -m "Add your feature"` then `git push origin feature/your-feature`
5. Open a pull request

If you'd like to suggest improvements or report bugs, feel free to [open an issue](https://github.com/your-username/your-repo/issues).
