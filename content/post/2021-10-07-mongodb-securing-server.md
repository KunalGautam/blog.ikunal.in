---
id: 154
title: MongoDB | Securing Server
author: Kunal Gautam
type: post
date: 2021-10-06T22:05:25+00:00
url: /kunal/2021/10/07/mongodb-securing-server/

categories:
  - MongoDB Learning
---

    use admin

    db.createUser({user:"adminUser",pwd:"adminPassword", roles:["userAdminAnyDatabase"]})

or

    db.createUser({
            user:"adminUser",
            pwd:"adminPassword",
            passwordDigestor:"server",
            roles:["dbOwner"]
        })

Add the following to `/etc/mongod.conf` or `/usr/local/etc/mongod.conf`

    security:
        authorization: enabled

Restart mongodb server

**To apply user with read write access to a database:**

1.  Switch to database you want to add user

    use kunal

2.  Then apply role

        db.createUser(
        {
            user: "kunal",
            pwd: "kunal",
            roles:[
                {
                    role: "readWrite",
                    db:"kunal"
                }]
        })
