# PostgresPersistence

`PostgresPersistence` is a [3rd party persistence class](https://github.com/python-telegram-bot/python-telegram-bot/wiki/Making-your-bot-persistent#3rd-party-persistence-classes) for [python-telegram-bot](https://python-telegram-bot.org/) that stores bot state in a Postgres database.

## Using persistence

First, set up a database through your preferred Postgres provider. (I used [Heroku](https://heroku.com/).) On this database, run:
```
CREATE TABLE telegram_persistence (id SERIAL PRIMARY KEY, updated TIMESTAMP DEFAULT NOW(), data BYTEA);
```

Then, construct a URL to your database of the form
```
postgres://username:password@hostname:port/database-name
```
and pass it to `PostgresPersistence`, and pass the resulting persistence object
to your `Updater` like so:

```
db_persistence = PostgresPersistence(postgres_url=DATABASE_URL)
updater = Updater(token=API_KEY, persistence=db_persistence)
```

## Examples

  * [Ranked Pairs](https://github.com/ncurrault/ranked-pairs-telegram)

## TODOs

  * more testing
  * prevent table from growing forever
  * proper library formatting for PyPI
