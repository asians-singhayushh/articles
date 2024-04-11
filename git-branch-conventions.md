> Summary of the architecture of git branches from this article - https://nvie.com/posts/a-successful-git-branching-model/

Branching Conventions:

We should have two evergreen branches:

      - main
      - develop

- Feature Branches:
  - Create from: develop branch.
  - Naming convention: Anything except main, develop, release-*, or hotfix-*.
  - Merge back into: develop.
  - Example:
  
    ```
    git checkout -b feature-JIRA-01 develop
    git merge --no-ff feature-JIRA-01
    ```

- Release Branches:
  - Create from: develop branch.
  - Naming convention: release-*.
  - We can use the new release branch as staging before publishing to main
  - Merge back into: develop and main.
  - Example:
 
    ```
    git checkout -b release-1.2 develop
    git merge --no-ff release-1.2
    git tag -a 1.2
    ```

- Hotfix Branches:
  - Create from: main branch.
  - Naming convention: hotfix-*.
  - Merge back into: develop and main.
  - Example:
  
    ```
    git checkout -b hotfix-1.2.1 main
    git merge --no-ff hotfix-1.2.1
    git tag -a 1.2.1
    ```

General Instructions:
- Always pull and push to the origin repository.
- Use the --no-ff flag for merge commits to preserve branch history.
- Follow the provided naming conventions for branches.
- When merging, ensure the commit message reflects the changes made.
- Tag releases for easy reference in the future.
- Delete branches after merging and finishing their purpose.
- Regularly update local branches with changes from origin.
- Ensure a stable state before branching off new releases or hotfixes.
- Use descriptive commit messages to maintain clarity in the project history.

By adhering to these conventions, you'll ensure a smooth and organized Git workflow for your development projects.
