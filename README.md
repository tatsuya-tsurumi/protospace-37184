# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

# users テーブル

| Colum              | Type   |Options                 |
| -------------------| ------ | ---------------------- |
| email              | string | NOT NULL, unique: true |
| encrypted_password | string | NOT NULL               |
| name               | string | NOT NULL               |
| profile            | text   | NOT NULL               |
| occupation         | text   | NOT NULL               |
| position           | text   | NOT NULL               |

has_many :prototypes
has_many :comments

# prototypes テーブル

| Colum              | Type       |Options                     |
| -------------------| ------     | -------------------------- |
| title              | string     | NOT NULL                   |
| catch_copy         | text       | NOT NULL                   |
| concept            | text       | NOT NULL                   |
| user               | references | NOT NULL foreign_key: true |

belongs_to :user
has_many :comments

# comments テーブル

| Colum              | Type       |Options                     |
| -------------------| ------     | -------------------------- |
| content            | text       | NOT NULL                   |
| prototype          | references | NOT NULL foreign_key: true |
| user               | references | NOT NULL foreign_key: true |

belongs_to :prototype
belongs_to :user
