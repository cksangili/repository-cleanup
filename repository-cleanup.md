# Git Repository Management

## Objective

The objective of this assignment is to create an API that manages Git repositories on either GitLab or GitHub. The API should allow adding a list of repositories and automatically removing stale branches based on specified criteria.

## Requirements

1. **API Development**:
    - The API should have the following endpoints (an [OpenAPI contract](./openapi.yaml) is provided for your reference):
        - **Add Repositories**: Register a list of repositories for stale branch management.
        - **Remove Repositories**: Unregister a list of repositories from stale branch management.
        - **List Repositories**: Display the repositories, their cleanup statuses, and the datetime (SGT) of the scheduled cleanup for stale branches.

1. **Background Service**:
    - A background service/job that periodically (e.g., every 1 hour) checks the repositories and removes stale branches based on the specified criteria.

    - Stale branch removal criteria: Automatically remove unprotected Git branches based on the following conditions:
        - They are stale for > 1 month and are not ahead of the default branch.
        - They are stale for > 6 months and are ahead of the default branch by no more than 1 commit.
        - They are stale for > 12 months and are ahead of the default branch by no more than 2 commits.

### User Interaction Flow

1. User accesses the API to add a list of repositories.
1. The background service periodically checks the repositories and removes stale branches based on the specified criteria.
1. User accesses the API to view the status of the repository management operations.
1. User accesses the API to remove a list of repositories.
