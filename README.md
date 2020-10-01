## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| nickname | string | null: false |
| email    | string | null: false , unique:true|
| password | string | null: false|
| last_name | string | null:false|
| first_name | string | null:false|
| last_name_kana | string | null:false|
| first_name_kana | string |null:false|
| birth_date | date | null:false|

### Association

- has_many :items
- has_many :comments
- has_many :purchases

## items テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name | string | null:false|
| explanation | text |  null:false|
| category_id | integer | null:false|
| condition_id | integer | null:false|
| postage_id | integer | null:false|
| prefecture_id | integer | null:false|
| handing_time_id | integer | null:false|
| price | integer | null:false|
| user | references | null:false, foreign_key:true|

### Association

has_one :purchase
belongs_to :user

## comments テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| comment | text | null:false|
| user | references | null:false, foreign_key:ture|
| item | references | null:false, foreign_key:ture|

### Association

belongs_to :user
belongs_to :item


## purchases テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| item | references | null:false, foreign_key:ture|
| user | references | null:false, foreign_key:ture|

### Association

belongs_to :user
belongs_to :item
has_one :address

## addresses テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| post_code | string | null:false|
| prefecture_id | integer | null:false|
| city | string | null:false|
| home_number | string | null:false|
| building_name | string ||
| phone_number | string | null:false|
| purchase | references | null:false, foreign_key:ture|

### Association

belongs_to :purchase

