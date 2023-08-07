# Sample Users Management Service

Sample users management application

## Development Setup

### Create new application

Create new github repositry for your application and clone it, so init the package and push
your very early setup code:

```sh
git clone `git@github.com:{your_github_username}/{your_repository_name}.git`
cd your_repository_name
cargo init
git add .
git commit -m "feat: create application package"
git push
```

### Dependencies

Installing application dependencies.

#### Environment Variables

Add the dotenvy library for easily use environment variables
```sh
cargo add dotenvy
```

#### Persistence

As this application should manage users it should to store the user data too. For this project we will use an relational database
managed by `PostgreSQL`; a very robust and open source sql database server. So we will add some tools to help us with database stuff
like connect to server, execute sql scripts, migrations for database versioning and more. For that we will use Diesel a very powerful
crate that provides all the features we will need to implements our users managemtn application. Lets add the diesel crate to the project:

```sh
cd sample_app
cargo add diesel
```

##### Diesel CLI
Install Diesel CLI. It will help you to manage your project. Use this to install Diesel CLI with only postgres:

```sh
sudo apt-get install libpq-dev
cargo install diesel_cli --no-default-features --features postgres
```

If everything gone well, now you can find a new `diesel.toml` file and  `migrations` directory in the project root.

##### Running Database Server

This project contains a docker-compose file that helps you to run the database server, so to get your db server up and running
just run. And of course you shouldnt have any previous contact with docker or docker-compose just install these programs and run the command:

```sh
docker-compose up -d
```

##### Setup Diesel

Be sure your local SQL Server is running an then run setup Diesel in your project by running:

```sh
diesel setup
```

##### Create new Table

Create new table with migrations. And use diesel cli to create migrations:

```sh
diesel migration generate user
```

Diesel created up.sql and down.sql files for us to apply and revert database changes.

So lets write SQL commands for `up.sql`:

```SQL
CREATE TABLE user (
    id UUID NOT NULL primary key,
    email VARCHAR NOT NULL,
    password VARCHAR NOT NULL,
    active BOOLEAN NOT NULL DEFAULT TRUE
)
```

and then for `down.sql`:

```SQL
DROP TABLE user;
```

Now apply migration:

```sh
diesel migration run
```

## Implement Rust App