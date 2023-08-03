# Markdown Word Counter GitHub Action: Documentation

This documentation is intended to guide you through the usage of the Markdown Word Counter GitHub Action in the context of this repository. This GitHub Action is designed to count and print the total number of words in each Markdown file (with the `.md` extension) located in the `courses` directory and all its subdirectories. This action does not count words in non-Markdown files.

## Requirements

You need administrative permissions on the repository. 

## Overview

The Markdown Word Counter GitHub Action is implemented as a workflow in our GitHub repository and is triggered each time a pull request is created. The workflow file, [markdown-word-counter.yml](.github/workflows/markdown-word-counter.yml), resides in the repository's `.github/workflows` directory. 


Outline of the workflow:

1. **Trigger**: Initiated by creating a pull request.
2. **Environment**: Run on the latest version of Ubuntu.
3. **Steps**: Consists of four main steps: code checkout, word count calculation and display, creating a PR comment, and handling potential failures.

    - **[Code Checkout](https://github.com/poojasekhar/Markdown-Word-Counter/blob/5a2db0910361499be10f112441ca5efa17d5f9eb/.github/workflows/markdown-word-counter.yml#L9-L10):** This step uses `actions/checkout@v2` to check-out the repository. 
    - **[Word Count Calculation and Display](https://github.com/poojasekhar/Markdown-Word-Counter/blob/2973118242d4d23d670d516b1dea4aca6d6489f8/.github/workflows/markdown-word-counter.yml#L12-L26):** This step iterates over all Markdown files within the `courses` directory and its subdirectories. For each file, it calculates the word count and prints it. It also keeps track of the total word count across all files and prints it at the end.
    - **[Create PR Comment](https://github.com/poojasekhar/Markdown-Word-Counter/blob/2973118242d4d23d670d516b1dea4aca6d6489f8/.github/workflows/markdown-word-counter.yml#L28-L40):** This step uses `actions/github-script@v5` to create a comment on the pull request with the word count results.
    - **[Handle Failure](https://github.com/poojasekhar/Markdown-Word-Counter/blob/2973118242d4d23d670d516b1dea4aca6d6489f8/.github/workflows/markdown-word-counter.yml#L42-L47):** This step handles any failure in the word count step and comments on the pull request about the failure.

## How to Trigger the GitHub Action

The Markdown Word Counter GitHub Action is set to trigger automatically for any new Pull Request created in the repository. Here's the general workflow:

1. Create a new branch.
2. Make any changes.
3. Create a pull request from your branch to the `main` branch. 

Once the pull request is created, the Markdown Word Counter GitHub Action will be triggered.

## Interpreting the Output

Upon completion of the GitHub Action, it will provide output in the GitHub Action log. It will display the word count for each Markdown file processed and the total word count across all the processed files.

After a Pull Request has triggered the GitHub Action:

1. Navigate to the `Actions tab` in your GitHub repository.
2. Click on the `Markdown Word Counter Action` from the workflow list.
3. Choose the workflow run from the list which corresponds to your recent Pull Request.
4. Under `Jobs`, click on the `count-words-on-markdown-file` job to view the details.
5. The `Word Count Calculation and Display` step will display the word counts. Here, you will see the number of words in each Markdown file as well as the total word count across all Markdown files in the `courses` directory and its subdirectories.

Moreover, upon completion of the GitHub Action, it will comment on the pull request with the detailed word count of each Markdown file and the total word count. This comment can be viewed directly in your pull request's 'Conversation' tab. This allows for easy access to the results without the need to navigate through the GitHub Action logs.

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
