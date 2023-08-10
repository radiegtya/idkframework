---
sidebar_position: 3
---

# API Guideline

As a contributor, you must follow our API rule, naming convention, methods, params, response, and much more. This guide will explain how to make a good API. To make all boilerplate consistent, you should follow this API outputs:

```
swagger refference: https://nestjs-stg.dumbways.id/docs
```

## Posts API 

### 1. [GET] /api/v1/posts
return all posts array []

### 2. [GET] /api/v1/posts/connection
return all posts array [] with aggregation (count, pagination, etc), inside an object {}

### 3. [GET] /api/v1/posts/{id}
return single post object {} by id

### 4. [POST] /api/v1/posts
create a post

### 5. [PATCH] /api/v1/posts/{id}
update a post by id. You can also use this endpoint for connecting/linking to relation. For example inside body, you can connect post to user:
```
{
  "user": {"connect": {"id": "UUID"}}
}
```

### 6. [DELETE] /api/v1/posts/{id}
delete a post by id

### 7. [POST] /api/v1/posts/many
create many posts

### 8. [PATCH] /api/v1/posts/many
update many posts, accept where, and data body

### 9. [DELETE] /api/v1/posts/many
delete many posts, accept where, and data body

---

## Upload API 
### 1. [POST] /api/v1/upload
upload a file and return string url (use object storage such as aws s3 or minio)

---

## Replies API 

### 1. [GET] /api/v1/replies
return all replies array []

### 2. [GET] /api/v1/replies/connection
return all replies array [] with aggregation (count, pagination, etc), inside an object {}

### 3. [GET] /api/v1/replies/{id}
return single reply object {} by id

### 4. [POST] /api/v1/replies
create a reply

### 5. [PATCH] /api/v1/replies/{id}
update a reply by id. 

### 6. [DELETE] /api/v1/replies/{id}
delete a reply by id

### 8. [PATCH] /api/v1/replies/many
update many replies, accept where, and data body

### 9. [DELETE] /api/v1/replies/many
delete many replies, accept where, and data body

---

## Users API (admin only)

### 1. [GET] /api/v1/users
return all users array []

### 2. [GET] /api/v1/users/connection
return all users array [] with aggregation (count, pagination, etc), inside an object {}

### 3. [GET] /api/v1/users/{id}
return single user object {} by id

### 4. [POST] /api/v1/users
create a user

### 5. [PATCH] /api/v1/users/{id}
update a user by id. 

### 6. [DELETE] /api/v1/users/{id}
delete a profile by id

---

## Profiles API 

### 1. [GET] /api/v1/profiles
return all profiles array []

### 2. [GET] /api/v1/profiles/connection
return all profiles array [] with aggregation (count, pagination, etc), inside an object {}

### 3. [GET] /api/v1/profiles/{id}
return single profile object {} by id

### 4. [POST] /api/v1/profiles
create a profile

### 5. [PATCH] /api/v1/profiles/{id}
update a profile by id. You can also use this endpoint for connecting/linking to relation. For example inside body, you can connect post to user:
```
{
  "user": {"connect": {"id": "UUID"}}
}
```

### 6. [DELETE] /api/v1/profiles/{id}
delete a profile by id

---

## Auth API 

### 1. [POST] /api/v1/register
register an user

### 2. [POST] /api/v1/login
log the user in (using jwt strategy)

### 3. [POST] /api/v1/logout
log the user out

---

## General Sample for Parameters & Response on GET method
parameters
```json
{
    //note: use select or include separately
    "select": {
        "title": true,
        "content": true
    },
    "include": {
        "replies": true,
        "createdBy": true
    },
    "orderBy": {
        "createdBy": {
            "email": "asc"
        }
    },
    "where": {
        "title": {
            "equals": "This is my post"
        }
    },
    "take": 5,
    "skip": 1,
    "cursor": "UUID_STRING",
    "distinct": [
        "title",
        "createdById"
    ]
}
```

response
```json
[
  {
    "id": "a7cb491f-6123-4090-98aa-6704c9836e3a",
    "title": "Post by Ega Radiegtya",
    "content": "this is my crazy content",
    "createdAt": "2023-08-09T09:42:16.271Z",
    "updatedAt": "2023-08-09T09:42:16.271Z",
    "createdById": "94305f93-e248-4f3b-b45b-f233cb1ec026",
    "updatedById": null,
    "replies": [],
    "createdBy": {
      "id": "94305f93-e248-4f3b-b45b-f233cb1ec026",
      "email": "radiegtya@gmail.com",
      "name": "Ega Radiegtya",
      "password": "$2a$10$8jPLW6yHsHCHnKgsdMccluGJym7R/OjLlrxH0a8maniFAvv6bF2/K",
      "createdAt": "2023-08-09T09:37:51.883Z",
      "updatedAt": "2023-08-09T09:37:51.883Z"
    }
  },
  {
    "id": "6c976b04-05dc-4a6e-8154-0c82ecc21b59",
    "title": "Today news is confusing",
    "content": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
    "createdAt": "2023-08-09T14:52:12.783Z",
    "updatedAt": "2023-08-09T14:52:12.783Z",
    "createdById": "94305f93-e248-4f3b-b45b-f233cb1ec026",
    "updatedById": null,
    "replies": [
      {
        "id": "d9c4bc97-7632-49ba-b1dd-43e7cfdbfc04",
        "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec efficitur interdum mauris, ut laoreet dui auctor eget. Phasellus et auctor magna",
        "postId": "6c976b04-05dc-4a6e-8154-0c82ecc21b59",
        "createdAt": "2023-08-09T15:08:42.033Z",
        "updatedAt": "2023-08-09T15:08:42.033Z",
        "createdById": "94305f93-e248-4f3b-b45b-f233cb1ec026",
        "updatedById": null
      }
    ],
    "createdBy": {
      "id": "94305f93-e248-4f3b-b45b-f233cb1ec026",
      "email": "ilhamadiputra4@gmail.com",
      "name": "Iruha-sama",
      "password": "$2a$10$8jPLW6yHsHCHnKgsdMccluGJym7R/OjLlrxH0a8maniFAvv6bF2/K",
      "createdAt": "2023-08-09T09:37:51.883Z",
      "updatedAt": "2023-08-09T09:37:51.883Z"
    }
  }
]
```
