# AI Repo Packer

AI Repo Packer is a bash script that condenses a code repository or directory into a single, AI-friendly file. This tool is designed to facilitate the process of feeding codebases to Large Language Models (LLMs) or other AI tools like Claude, ChatGPT, and Gemini.

## Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Output Format](#output-format)
- [Git Awareness](#git-awareness)
- [File Exclusion](#file-exclusion)
- [Limitations and Considerations](#limitations-and-considerations)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Repository/Directory Packaging**: Packs an entire repository or directory structure into a single file.
- **Git-Aware**: Respects .gitignore rules when processing files in a Git repository.
- **File Exclusion**: Allows specifying files or patterns to exclude, with some default exclusions.
- **AI-Oriented Format**: Structures the output in a way that's intended to be easy for AI models to process.
- **Simple Token Counting**: Provides a basic word-count approximation for each file and the entire repository/directory.
- **Directory Structure Visualization**: Attempts to provide a tree-like view of the directory structure.
- **File Content Preservation**: Includes the full content of each file in the output.

## Requirements

- Bash shell
- `tree` command (optional, falls back to `find` if not available)
- Git (optional, for .gitignore support)

## Installation

1. Download the `ai-repo-packer.sh` script.
2. Make the script executable:

   ```bash
   chmod +x ai-repo-packer.sh
   ```

3. Optionally, move the script to a directory in your PATH for easy access:

   ```bash
   sudo mv ai-repo-packer.sh /usr/local/bin/ai-repo-packer
   ```

## Usage

Run the script by providing the path to your repository or directory:

```bash
./ai-repo-packer.sh [options] <path_to_your_repository_or_directory>
```

Options:

- `-e <pattern>`: Exclude files matching the specified pattern. Can be used multiple times.
- `-h`: Display help message.

Examples:
```bash
# Basic usage
./ai-repo-packer.sh /path/to/your/repo

# Exclude specific files
./ai-repo-packer.sh -e "*.log" -e "temp_*" /path/to/your/repo

# Display help
./ai-repo-packer.sh -h
```

The script will generate a file named `ai_friendly_repo_pack.txt` in the current directory.

## Output Format

The generated file has the following structure:

1. Header with metadata and AI instructions
2. Directory structure (limited to 3 levels deep)
3. Files, each with:

   - File path
   - Simple token (word) count
   - File contents

4. Total token (word) count for the entire repository/directory

## Git Awareness

When run on a Git repository:

- The script respects .gitignore rules, excluding files that would be ignored by Git.
- The .git directory is always excluded from processing.

When run on a non-Git directory:

- All files are included except for hidden files and directories (those starting with a dot) and explicitly excluded files.

## File Exclusion

By default, the script excludes the following files:

- README.md
- LICENSE
- .editorconfig
- All Markdown files (*.md)

You can specify additional files or patterns to exclude using the `-e` option. Exclusion patterns use bash filename expansion syntax.

## Limitations and Considerations

- **Token Counting**: The script uses a simple word-count approach, which may not accurately reflect the tokenization used by specific AI models.
- **Directory Structure**: The directory structure visualization is limited to 3 levels deep when using the `tree` command.
- **Large Repositories**: For very large repositories/directories, the output file may become unwieldy and exceed the context limits of some AI models.
- **Git Dependency**: Full .gitignore support requires Git to be installed and available in the system PATH.

## Customization

While the script provides command-line options for basic customization, you can also modify the script directly to:

- Adjust the token counting method
- Change default file inclusion/exclusion rules
- Modify the output format or included information

Note that direct script customization requires editing the bash script and may require bash scripting knowledge.

## Contributing

Contributions to improve AI Repo Packer are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them with clear, descriptive messages.
4. Push your changes to your fork.
5. Submit a pull request with a clear description of your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions, suggestions, or issues, please open an issue in the GitHub repository.
