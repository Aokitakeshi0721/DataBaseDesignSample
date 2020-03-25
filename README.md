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


* Configuration
* Database creation
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|text|null: false|
|Email|integer|null: false, add_index :users, :email, unique: true|
|password|integer|null: false, pass.match(/[a-z\d]{8,}/i)| 

### Association
- has_many :groups_users
- has_many :message


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|text|null: false, |

### Association
- has_many :groups_users
- has_many :message


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## messageテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
