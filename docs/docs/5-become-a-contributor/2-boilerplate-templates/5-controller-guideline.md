---
sidebar_position: 3
---

# Controller Guideline


### 1. Naming Convention
Your controller should use plural naming convention, and should matches to your table name. For example, you have table named "posts", your controller should be named with "PostsController".

### 2. Coding Guideline
Your controller should be as slim as possible, and act just for receiving request, passing params, and sending response. While your complex logic should be inside of "Service" file