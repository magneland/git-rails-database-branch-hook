git-rails-database-branch-hook
==============================

Save and restore the state of your Rails development and test databases as you work on different branches.

This allows you to make some changes to the structure of your database on a feature branch, then be able to quickly switch back to your master branch to make a hotfix or start a new feature branch with your original database structure and content.

# Installation

Download the `post-checkout` file into the `.git/hooks` directory of your project. Be sure to keep the `post-checkout` name to match Git's expectations.

Alternatively, you can clone this repository to your computer then symlink the `post-checkout` file into the `.git/hooks` directory of each of your projects. This allows you to manage the file in one place and be able to easily pull down updates.

# Support

Only PostgreSQL and MySQL databases are currently supported.

# Non-Rails Usage

While this hook is geared towards Rails and depends on Ruby, it is very easy to use it in non-Ruby/Rails projects, so long as you have Ruby installed on your system.

This script will look for a `config/database.yml` file in your project's root directory, and expects it to look like this:

```yaml
development:
  adapter: <adapter>
  username: <database username>
  password: <database password>
  database: <database name>
```

We currently support two adapters: `mysql2` and `postgresql`. We don't actually rely on these gems, but instead use them to determine which database's command line tools we should use (mysqldump/mysql or pg_dump/psql). Use `mysql2` if you are using a MySQL database, or `postgresql` if you are using a PostgreSQL database.
