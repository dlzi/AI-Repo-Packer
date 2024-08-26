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
- [Prompt Examples](#prompt-examples)
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

## Prompt Examples

After using AI Repo Packer to condense your codebase into a single, AI-friendly file, you're ready to harness the power of advanced AI tools for comprehensive code analysis and improvement. This section provides a curated set of prompts designed to maximize the utility of your packed repository when working with AI assistants such as Claude, ChatGPT, and Gemini.

These prompts are crafted to address various aspects of software development, from high-level architecture review to detailed code quality assessment. By using these prompts as starting points, you can effectively communicate your needs to AI models and extract valuable insights about your codebase.

### How to Use These Prompts

1. Begin by uploading your AI Repo Packer output file to your chosen AI tool.
2. Copy the desired prompt from the examples below.
3. Paste the prompt into your conversation with the AI, adjusting it as needed for your specific requirements.
4. Engage with the AI's responses, asking follow-up questions to delve deeper into particular areas of interest.

Remember, these prompts are starting points. Feel free to modify them or combine elements from different prompts to best suit your project's unique needs. The more specific and detailed your prompts, the more tailored and actionable the AI's responses will be.

Let's explore some example prompts to kickstart your AI-assisted code analysis:

#### Code Review and Refactoring:

```
This file contains my entire codebase. Please perform a comprehensive code review focusing on the following aspects:

1. Overall architecture and design patterns
2. Code organization and modularity
3. Naming conventions and code readability
4. Error handling and edge cases
5. Performance considerations

For each aspect, provide:

a) Specific examples of good practices already in use
b) Areas that need improvement, with code snippets where applicable
c) Refactoring suggestions to enhance maintainability and scalability
d) Any potential security vulnerabilities

Conclude with a summary of the top 3-5 most impactful refactoring recommendations.
```

#### Documentation Generation:

```
Based on the codebase in this file, please generate a detailed README.md that includes:

1. Project title and a brief, compelling description
2. Badges (if applicable) for build status, test coverage, etc.
3. Key features with brief explanations
4. Technologies/frameworks used
5. Detailed installation and setup instructions, including prerequisites
6. Usage examples with code snippets
7. API Reference (if applicable)
8. Configuration options
9. Contributing guidelines
10. License information
11. Acknowledgments (if any)

Please format the README using proper Markdown syntax, including headings, code blocks, and lists where appropriate.
```

#### Test Case Generation:

```
Analyze the code in this file and generate a comprehensive set of unit tests. For each main function or class:

1. Identify the critical paths and functionalities to be tested
2. Provide a list of test cases, including:
   a) Normal operation scenarios
   b) Edge cases (e.g., empty inputs, maximum values)
   c) Error scenarios and exception handling
3. For each test case, specify:
   a) Input values
   b) Expected output or behavior
   c) The assertion to be made
4. Suggest any mock objects or stubs that might be needed
5. Identify any parts of the code that might be challenging to test and suggest potential solutions

Please provide the test cases in a format that could be easily translated into actual unit tests in the appropriate testing framework.
```


#### Code Quality Assessment:

```
Review the codebase for adherence to coding best practices and industry standards. Please provide a detailed analysis covering:

1. Code style and consistency
   a) Adherence to language-specific style guides
   b) Consistent naming conventions
   c) Proper indentation and formatting
2. Code complexity
   a) Identify overly complex methods or classes
   b) Suggest ways to reduce complexity (e.g., breaking down large functions)
3. DRY (Don't Repeat Yourself) principle adherence
   a) Identify repeated code patterns
   b) Suggest abstractions or refactoring to reduce repetition
4. SOLID principles application
   a) Evaluate how well the code follows SOLID principles
   b) Suggest improvements for better adherence
5. Error handling and logging
   a) Assess the effectiveness of current error handling
   b) Suggest improvements in error reporting and logging
6. Performance considerations
   a) Identify potential performance bottlenecks
   b) Suggest optimizations
7. Security best practices
   a) Identify any security vulnerabilities
   b) Suggest security improvements

For each point, provide specific code examples and suggested improvements. Conclude with a prioritized list of the top 5 areas for improvement.
```

#### Library Overview:

```
This file contains the entire codebase of the library. Please provide a comprehensive overview including:

1. Main purpose and problem the library solves
2. Key features and capabilities
3. Overall architecture
   a) Major components/modules and their responsibilities
   b) How these components interact
4. Core abstractions and design patterns used
5. Public API overview
   a) Main classes/functions that users of the library would interact with
   b) Brief description of what each does
6. Any notable algorithms or data structures used
7. Dependencies and integration points with other systems/libraries
8. Scalability and performance characteristics
9. Potential use cases or example scenarios where this library would be particularly useful
10. Any unique or innovative approaches used in the implementation

Please provide code snippets or class/function names as examples where relevant. Conclude with a brief comparison to similar libraries in the ecosystem, highlighting this library's unique strengths.
```



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
