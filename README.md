<p align='center'>
  <a href="https://mike.works" target='_blank'>
    <img height=40 src='https://assets.mike.works/img/login_logo-33a9e523d451fb0d902f73d5452d4a0b.png' />
  </a> 
</p>
<p align='center'>
  <a href="https://mike.works/course/sql-fundamentals-ad811af" target='_blank'>
    <img height=150 src='https://user-images.githubusercontent.com/558005/33009968-b8a0ea60-cd7c-11e7-81af-b48a6273b12b.png' />
  </a>
</p>
<p align='center'>
  <a href="https://travis-ci.org/mike-works/sql-fundamentals?branch=solutions-pro" title="Build Status">
    <img title="Build Status" src="https://travis-ci.org/mike-works/sql-fundamentals.svg?branch=solutions-pro"/>
  </a>
  <a href="https://mike.works/course/sql-fundamentals-ad811af" title="SQL Fundamentals">
    <img title="Course Outline" src="https://img.shields.io/badge/mike.works-course%20outline-blue.svg"/>
  </a>
  <a href="https://docs.mike.works/sql-slides" title="Slides">
    <img title="Slides" src="https://img.shields.io/badge/mike.works-slides-blue.svg"/>
  </a>
  <a title='GreenKeeper'>
    <img title='GreenKeeper' src='https://badges.greenkeeper.io/mike-works/sql-fundamentals.svg'>
  </a>
</p>
<p align='center'>
This is the example project used for the <a title="Mike.Works" href="https://mike.works">Mike.Works</a> <a title="SQL Fundamentals" href="https://mike.works/course/sql-fundamentals-ad811af">SQL Fundamentals</a> course.
</p>

# What are we building?

We'll be working with several flavors of the [Northwind Database](https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/sql/linq/downloading-sample-databases), which Microsoft uses to demonstrate a wide range of features across their MS Access and MS SQL Server product lines. You'll be writing some application code in a small [Node.js](https://nodejs.org) web application (built with [Express](https://expressjs.com)) to view and make changes to this data.

Here's what it looks like (and [here](https://damp-oasis-38940.herokuapp.com/) is a live demo):

<p align="center">
<img height=400 src="https://user-images.githubusercontent.com/558005/35312473-7646b68c-0070-11e8-83df-25800047b763.png" />
</p>

This app is not in a good state at the beginning of the workshop. Features are missing, there are major performances, and quite a few database-related bugs. We'll fix all these problems and learn as we go!

# Setup Instructions

## Clone this project

In your terminal, run

```sh
git clone https://github.com/mike-works/sql-fundamentals sql
cd sql
```

## Database Setup

This project is used for two workshops. [SQL Fundamentals](https://mike.works/course/sql-fundamentals-ad811af) may be completed using either SQLite or PostgreSQL, and [Professional SQL](https://mike.works/course/professional-sql-c9c7184) requires PostgreSQL.

To set up the database software, please check out these guides

* [Installing SQLite 3](./SQLITE_SETUP.md)
* [Installing Postgres 10](./POSTGRES_SETUP.md)

## Install dependencies

If you only intend to complete the [SQL Fundamentals](https://mike.works/course/sql-fundamentals-ad811af) workshop (exercises 1-10), you can run

```sh
npm install --no-optional
```

If you wish to proceed beyond exercise 10 for the [Professional SQL](https://mike.works/course/professional-sql-c9c7184) course, please include optional dependencies

```sh
npm install
```

## Seed Data

If you're using the _SQLite_ database, the `./master.sqlite` file already contains the data we'll be working with. Please run

```sh
npm run db:setup:sqlite
```

If you're using the _PostgreSQL_ database, the `./northwind.sql` script contains the necessary commands for setting up the equivalent data. Please run

```sh
npm run db:setup:pg
```

## Run the tests

There's an initial set of tests that ensure the app is correctly setup for the beginning of the course. You should be able to run this command and see them all passing

```sh
# Test against SQLite
npm run test:ex 0
# Test against PostgreSQL
DB_TYPE=pg npm run test:ex 0
```

Or, if you wish to have the app watch the source code for changes, and re-run the tests on each save...

```sh
# Test against SQLite
npm run test:ex:watch 0
# Test against PostgreSQL
DB_TYPE=pg npm run test:ex:watch 0
```

## Start the app

```sh
# Run w/ SQLite
npm run watch
# Run w/ PostgreSQL
DB_TYPE=pg npm run watch
```

# Deploy this app on heroku

If you don't want to set up your own [PostgreSQL](https://www.postgresql.org) database locally, you can deploy this app onto heroku and use their $7/month hosted PostgreSQL service.

### Step 1

Click this button to deploy the app to heroku. Because the database is large (about 700K rows) it cannot be run with their free database option.
[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

### Step 2

Populate the database with data. This can be done one of two ways

#### If you have a local database already setup and running

Use the heroku toolbelt posgtres push utility (recommended)

```sh
heroku pg:push northwind DATABASE_URL --app replace-this-with-your-heroku-app-name
```

#### If you don't have a local database to push

Use the `psql` command line utility to run the huge PostgreSQL setup script. This will take at least several minutes.

```sh
heroku run "psql \$DATABASE_URL?ssl=true < northwind.sql -q" --app sql456
```

# Build Status

| Solutions Branch                                                                               | Status                                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [SQL Fundamentals](https://github.com/mike-works/sql-fundamentals/tree/solutions-fundamentals) | [![Build Status](https://travis-ci.org/mike-works/sql-fundamentals.svg?branch=solutions-fundamentals)](https://travis-ci.org/mike-works/sql-fundamentals?branch=solutions-fundamentals) |
| [SQL Pro](https://github.com/mike-works/sql-fundamentals/tree/solutions-pro)                   | [![Build Status](https://travis-ci.org/mike-works/sql-fundamentals.svg?branch=solutions-pro)](https://travis-ci.org/mike-works/sql-fundamentals?branch=solutions-pro)                   |

# License

While the general license for this project is the BSD 3-clause, the exercises
themselves are proprietary and are licensed on a per-individual basis, usually
as a result of purchasing a ticket to a public workshop, or being a participant
in a private training.

Here are some guidelines for things that are **OK** and **NOT OK**, based on our
understanding of how these licenses work:

### OK

* Using everything in this project other than the exercises (or accompanying tests)
  to build a project used for your own free or commercial training material
* Copying code from build scripts, configuration files, tests and development
  harnesses that are not part of the exercises specifically, for your own projects
* As an owner of an individual license, using code from tests, exercises, or
  exercise solutions for your own non-training-related project.

### NOT OK (without express written consent)

* Using this project, or any subset of
  exercises contained within this project to run your own workshops
* Writing a book that uses the code for these exercises
* Recording a screencast that contains one or more of this project's exercises

# Copyright

&copy; 2018 [Mike.Works](https://mike.works), All Rights Reserved

###### This material may not be used for workshops, training, or any other form of instructing or teaching developers, without express written consent
