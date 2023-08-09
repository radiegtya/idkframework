---
sidebar_position: 4
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Sending Pull Request

## Creating the Pull Request

1. On GitHub.com, navigate to the main page of the repository.
2. In the "Branch" menu, choose the branch that contains your commits.
3. Above the list of files, in the yellow banner, click Compare & pull request to create a pull request for the associated branch.
4. Use the base branch dropdown menu to select the branch you'd like to merge your changes into, then use the compare branch drop-down menu to choose the topic branch you made your changes in.
5. Type a title and description for your pull request.
6. To create a pull request that is ready for review, click Create Pull Request. To create a draft pull request, use the drop-down and select Create Draft Pull Request, then click Draft Pull Request.

:::info

For more details you can read from GitHub Docs :
1. [about pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests?platform=windows)
2. [creating pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)

:::

## Pull Request Naming Convention 
### Important to Know
Consists of two parts:

1. Title
    - Short and descriptive summary
    - Start with corresponding ticket/story id (e.g. from Jira, GitHub issue, etc.)
    - Should be capitalized and written in imperative present tense
    - Not end with period
2. Description
    - Separated with a blank line from the subject
    - Explain what, why, etc.
    - Each paragraph capitalized

:::note

**Title** is about short informative summary of the pull request <br/>
**Description** is about detailed explanatory text describing the PR for the reviewer

:::


### Example



<Tabs>
  <TabItem value="apple" label="Title">#CLS-23 Added Search Feature By Username</TabItem>
  <TabItem value="orange" label="Description">
  I want to contribute by adding a search feature by username on the main page. This feature will allow users to find community members more easily. Here are the details of the changes I made: <br/>
    - Added search input at the top of the member list.<br/>
    - Implements search logic using JavaScript.<br/>
    - Add appropriate layouts and styles.<br/>
I have tested this feature locally and the changes tested fine. Please review and include if deemed appropriate.</TabItem>
</Tabs>