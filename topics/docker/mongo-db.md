# MongoDB with Docker

## Launch Instance

```zsh
docker run --name mongo-sample -p 27017:27017 mongo
# Access it via mongodb://localhost:27017
```

## Custom Mongo Configuration

```zsh
docker run --name mongo-sample -p 27017:27017 -v /path/to/custom/mongod.conf:/etc/mongod.conf mongo
```

```txt
# mongod.conf

# other settings

# network interfaces
net:
  port: 27017
  # bindIp: 127.0.0.1   # default, localhost only
  bindIp: 0.0.0.0       # setup external ip binding

# other settings
```

Use a different port mapping via `-p 27117:27017` in the following command:

```zsh
docker run --name mongo-sample -p 27117:27017 -v /path/to/custom/mongod.conf:/etc/mongod.conf mongo
```

## Authentication

```yml
version: "3"

services:
  mongodb:
    image: mongo
    container_name: mongo-sample
    ports:
      - 27117:27017
    volumes:
      - ./mongod.conf:/etc/mongod.conf
    entrypoint: ["mongod", "--auth", "--config", "/etc/mongod.conf"]
```

Next access the container via:

```zsh
docker exec -it mongo-sample mongo
```

```zsh
use admin
db.createUser({
  user: 'super',
  pwd: 'SuperPassWordNotPublic',
  roles:['userAdminAnyDatabase']
})
```

Access the mongo shell via:

```zsh
mongodb://super:SuperPassWordNotPublic@0.0.0.0:27117
```

Add users via the super account:

```zsh
docker exec -it mongo-sample mongo -u super
```

Enter password and hit enter.

```zsh
# go to database `admin`
use admin

# add admin
db.createUser({
  user: 'admin',
  pwd: 'ComplexAdminPassword',
  roles:[
    { 
      role: 'readWrite',
      db: 'pages'
    }
  ]
})

# add reader "regular user"
db.createUser({
  user: 'reader',
  pwd: 'ReaderPassword',
  roles:[
    { 
      role: 'read',
      db: 'pages'
    }
  ]
})
```

```zsh
mongodb://admin:ComplexAdminPassword@0.0.0.0:27117
mongodb://reader:ReaderPassword@0.0.0.0:27117
```
