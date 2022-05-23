# copy-files-action
This GitHub Action copies some files, described by a string pattern, into another repository.

## Example Workflow
```yml
name: Push to Other Repo

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          persist-credentials: false
          fetch-depth: 0

      - name: Commit & Push
        uses: SimoneRomagnoli/copy-files-action@v1.0.4
        env:
          API_TOKEN_GITHUB: ${{ secrets.YOUR_SECRET }}
        with:
          pattern: "*.txt"
          dst_repo: "SimoneRomagnoli/repoName"
          dst_dir: "myFiles"
          dst_branch: "main"
          commit_msg: "Your custom commit message"
          user_name: "SimoneRomagnoli"
          user_email: "simone.romagnoli10@studio.unibo.it"
```

```IMPORTANT```: you have to set your personal secret in the repository the action is running on: it has to be set in the `Settings -> Secrets` section of your repository. 

## Action Parameters

* pattern: The string pattern to match on files you want to copy in another repository
* dst_repo: The destination repository
* dst_dir: The destination directory
* dst_branch: The destination branch (default: 'main')
* commit_msg: Your custom commit message
* user_name: The user that is performing the push operation
* user_email: The user's email

## License

The scripts and documentation in this project are released under the [MIT License](https://github.com/SimoneRomagnoli/copy-files-action/blob/main/LICENSE)

## Contributions

If you think there could be useful features that are not yet implemented or bugs that need to be fixed, please:

* Fork the repository;
* Make the changes you like;
* Make a pull request so that the feature/bug fix can be merged into this repository.