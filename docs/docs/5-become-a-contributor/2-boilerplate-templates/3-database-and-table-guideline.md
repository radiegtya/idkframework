---
sidebar_position: 3
---

# Database Design Guideline

for now please refer to this database design in graphql syntax 😅

```gql
model User {
  id             String    @id @default(uuid()) @db.Uuid()
  email          String    @unique
  name           String
  password       String
  roles          Role[]
  profile        Profile?
  followedBy     Follows[] @relation("following")
  following      Follows[] @relation("follower")
  posts          Post[]    @relation(name: "UserCreatedPosts")
  updatedPosts   Post[]    @relation(name: "UserUpdatedPosts")
  replies        Reply[]   @relation(name: "UserCreatedReplies")
  updatedReplies Reply[]   @relation(name: "UserUpdatedReplies")

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@map("users")
}

model Role {
  id    String @id @db.VarChar(20)
  name  String
  users User[]

  @@map("roles")
}

model Profile {
  id      String @id @default(uuid()) @db.Uuid()
  address String? @db.VarChar(255)
  user    User   @relation(fields: [userId], references: [id])
  userId  String @unique @db.Uuid()

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@map("profiles")
}

model Post {
  id      String  @id @default(uuid()) @db.Uuid()
  title   String  @db.VarChar(255)
  content String
  replies Reply[]

  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
  createdBy   User     @relation(name: "UserCreatedPosts", fields: [createdById], references: [id])
  createdById String   @db.Uuid()
  updatedBy   User?    @relation(name: "UserUpdatedPosts", fields: [updatedById], references: [id])
  updatedById String?  @db.Uuid()

  @@map("posts")
}

model Follows {
  follower    User   @relation("follower", fields: [followerId], references: [id])
  followerId  String @db.Uuid()
  following   User   @relation("following", fields: [followingId], references: [id])
  followingId String @db.Uuid()

  createdAt DateTime @default(now())

  @@id([followerId, followingId])
  @@map("follows")
}

model Reply {
  id      String @id @default(uuid()) @db.Uuid()
  content String
  post    Post   @relation(fields: [postId], references: [id])
  postId  String @db.Uuid()
  replies ReplyOnReply[] @relation(name:"reply")

  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
  createdBy   User     @relation(name: "UserCreatedReplies", fields: [createdById], references: [id])
  createdById String   @db.Uuid()
  updatedBy   User?    @relation(name: "UserUpdatedReplies", fields: [updatedById], references: [id])
  updatedById String?  @db.Uuid()

  @@map("replies")
}

model ReplyOnReply {
  reply           Reply     @relation(name:"reply", fields: [replyId], references: [id])
  replyId         String    @db.Uuid()

  @@id([replyId])
  @@map("reply_on_reply")
}
```