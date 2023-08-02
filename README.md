# Markdown Word Counter GitHub Action: Documentation

This documentation is intended to guide you through the usage of the Markdown Word Counter GitHub Action in the context of this repository. This GitHub Action is designed to count and print the total number of words in each Markdown file (with the `.md` extension) located in the `courses` directory and all its subdirectories. This action does not count words in non-Markdown files.

## Requirements

You need administrative permissions on the repository. A GitHub personal access token (PAT) with `public_repo` or `repo` (for private repositories) scope is required for creating comments on pull requests.

## Overview

The Markdown Word Counter GitHub Action is implemented as a workflow in our GitHub repository and is triggered each time a pull request is created. This workflow is defined in a YAML file under the `.github/workflows` directory.

Outline of the workflow:

1. **Trigger**: The workflow is initiated by creating a pull request.
2. **Environment**: The workflow is run on the latest version of Ubuntu.
3. **Steps**: The workflow consists of four main steps: code checkout, word count calculation and display, creating a PR comment, and handling potential failures.

    - **[Code Checkout](https://github.com/poojasekhar/Markdown-Word-Counter/blob/5a2db0910361499be10f112441ca5efa17d5f9eb/.github/workflows/markdown-word-counter.yml#L9-L10):** This step uses `actions/checkout@v2` to check-out the repository. 
    - **Word Count Calculation and Display:** This step iterates over all Markdown files within the `courses` directory and its subdirectories. For each file, it calculates the word count and prints it. It also keeps track of the total word count across all files and prints it at the end.
    - **Create PR Comment:** This step uses `actions/github-script@v5` to create a comment on the pull request with the word count results.
    - **Handle Failure:** This step handles any failure in the word count step and comments on the pull request about the failure.

## Workflow File

The workflow file, [markdown-word-counter.yml](.github/workflows/markdown-word-counter.yml), resides in the repository's `.github/workflows` directory. 

## How to Trigger the GitHub Action

The Markdown Word Counter GitHub Action is set to trigger automatically for any new Pull Request created in the repository. Here's the general workflow:

1. Create a new branch.
2. Make changes to the Markdown files in the `courses` directory and commit your changes.
3. Create a pull request from your branch to the `main` branch. 

Once the pull request is created, the Markdown Word Counter GitHub Action will be triggered.

## Interpreting the Output

Upon completion of the GitHub Action, it will provide output in the GitHub Action log. It will display the word count for each Markdown file processed and the total word count across all the processed files.

After a Pull Request has triggered the GitHub Action:

Navigate to the Actions tab in your GitHub repository.
Click on the Markdown Word Counter Action from the workflow list.
Choose the workflow run from the list which corresponds to your recent Pull Request.
Under Jobs, click on the count-words-on-markdown-file job to view the details.
The word counts will be displayed in the Word Count Calculation and Display step under Run actions/checkout@v2. Here, you will see the number of words in each Markdown file as well as the total word count across all Markdown files in the courses directory and its subdirectories.

Moreover, upon completion of the GitHub Action, it will comment on the pull request with the detailed word count of each Markdown file and the total word count. This comment can be viewed directly in the 'Conversation' tab of your pull request. This allows for easy access to the results without the need to navigate through the GitHub Action logs.

For each processed file, it will display a line like:

```
File <file-path> contains <word-count> words
```

And finally, it will display the total word count as:

```
Total words in markdown files: <total-word-count>
```

## Troubleshooting

In case of any errors or if the workflow run does not appear as expected, please check the error messages and the GitHub Action setup. If the issue persists, you can seek further assistance by opening an issue on the repository.

