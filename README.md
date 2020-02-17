# README

# chatspace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users_groups
- has_many :groups, through: :users_groups

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user|integer|null: false, foreign_key: true|
|group|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users_groups
- has_many :users, through: :users_groups

## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user|integer|null: false, foreign_key: true|
|group|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## reference型を使用
  下記をマイグレーションファイルに追加して作成
  t.references :user, foreign_key: true
  t.references :group, foreign_key: true