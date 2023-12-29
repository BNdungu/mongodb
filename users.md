# Setting Up Users in MongoDB

This guide outlines the steps to set up users in MongoDB using the `mongosh` shell in Ubuntu.

## Prerequisites

- MongoDB installed on your system. If not installed, follow the [official MongoDB installation guide](https://docs.mongodb.com/manual/administration/install-community/) for Ubuntu.

## Steps

### 1. Start MongoDB Server

Start the MongoDB server if it's not already running. Use the following command:

```bash
sudo service mongod start
```

### 2. Access MongoDB Shell (mongosh)

Open a terminal window and enter the MongoDB shell using the `mongosh` command:

```bash
mongosh
```

### 3. Access Administrative Database

Switch to the `admin` database. This is where user administration tasks are performed:

```javascript
use admin
```

### 4. Create Administrative User (if not exist)

If an admin user doesn't exist, create one using the following command:

```javascript
db.createUser({
  user: "adminUsername",
  pwd: "adminPassword",
  roles: ["root"]
})
```

Replace `"adminUsername"` and `"adminPassword"` with your desired admin username and password.

### 5. Authenticate as Admin User

Authenticate with the admin user created in the previous step:

```javascript
db.auth("adminUsername", "adminPassword")
```

### 6. Create Additional Users (Optional)

Create additional users with specific roles based on your application requirements:

```javascript
use yourDatabaseName
db.createUser({
  user: "username",
  pwd: "password",
  roles: [{ role: "readWrite", db: "yourDatabaseName" }]
})
```

Replace `"yourDatabaseName"`, `"username"`, and `"password"` with your database name and desired username/password.

### 7. Verify Users

List all users to verify their creation:

```javascript
show users
```

### 8. Exit the MongoDB Shell

Exit the `mongosh` shell:

```javascript
exit
```

## Additional Resources

- [MongoDB Documentation](https://docs.mongodb.com/manual/)
- [MongoDB University](https://university.mongodb.com/)



