# テーブル設計

## users テーブル

| Column               | Type   | Options     |
| -------------------- | ------ | ----------- |
| email                | string | null: false |
| encrypted_password   | string | null: false |
| name                 | string | null: false |
| profile              | text   | null: false |
| occupation           | text   | null: false |
| position             | text   | null: false |

### ASSOCIATION

- has_many :prototypes
- has_many :comments

## prototypes テーブル

| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| name         | string     | null: false                    |
| catch_phrase | string     | null: false                    |
| concept      | string     | null: false                    |
| image        | string     | null: false                    |
| user_id      | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many   :comments

## comments テーブル

| Column       | Type       | Options                        |
| ------------ | -----------| -------------------------------|
| text         | text       | null: false                    |
| user_id      | references | null: false, foreign_key: true |
| prototype_id | references | null: false, foreign_key: true |

### Association

- belongs_to :prototype
- belongs_to :user