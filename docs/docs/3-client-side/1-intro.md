---
sidebar_position: 1
---

# Introduction

IDKFramework work seamlessly with any front-end framework such as REACT, VUE, Angular, and much more. You can directly use our client side REST API + SDK on your client side front-end without worrying about the back-end and the security.


**REST API SAMPLE**
```json
GET /posts?where[createdBy][email][equals]=me@mail.com

[
    {
        "id": "4cc660fa-3675-11ee",
        "title": "Hello Everyone",
        "createdBy": {
            "email": "me@mail.com"
        }
    },
    {
        "id": "5aa77493-10d0-42fd",
        "title": "Hello My Subscriber",
        "createdBy": {
            "email": "me@mail.com"
        }
    }
]
```

**SDK Sample (REACT)**
```javascript
import { IDKClient } from "@idk/client"

const idk = new IDKClient()

const posts = idk.posts.find({
    where: {
        createdBy: {
            email: "me@mail.com"
        }
    }
})
```