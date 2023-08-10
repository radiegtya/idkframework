---
sidebar_position: 2
---

# Structuring Folder

**Your folder structure should include**
- Models #for database entities and validation (you can use entities/repositories/dto/anything depends on ORM technology)
- Routes (optional depends on Framework) #for routing the url
- Controllers #for passing params, get request, and send response
- Services  #for database queries, and logic

**folder structure sample:**
```
├───models
│   ├───post.model.js           #use singular naming convention
├───routes
│   ├───posts.route.js          #use plural naming convention
├───services
│   ├───posts.service.js        #use plural naming convention
├───controllers
│   ├───posts.controller.js     #use plural naming convention

```