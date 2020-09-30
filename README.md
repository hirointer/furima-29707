## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| nickname | string | null: false |
| email    | string | null: false , uniqueness:true|
| password | string | null: false ,uniqueness:true|
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
| category_id | references | null:false, foreign_key:ture|
| condition_id | integer | null:false|
| postage_id | integer | null:false|
| prefecture_id | integer | null:false|
| handing_time_id | integer | null:false|
| price | integer | null:false|
| user_id | references | null:false, foreign_key:ture|
| img_id | integer | null:false|

### Association

belongs_to :user
has_many :comments
has_many :item_imgs
has_one :purchase

## comments テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| comment | text | null:false|
| user | references | null:false, foreign_key:ture|
| item | references | null:false, foreign_key:ture|

### Association

belongs_to :user
belongs_to :item

## item_imgs テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| image | string | null:false|
| item | references | null:false, foreign_key:ture|

### Association

belongs_to :item

## purchases テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| item | references | null:false, foreign_key:ture|
| user | references | null:false, foreign_key:ture|

### Association

belongs_to :user
belongs_to :item

## addresses テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| post_code | string | null:false|
| prefecture_id | integer | null:false, foreign_key:ture|
| city | string | null:false|
| home_number | string | null:false|
| building_name | string ||
| phone_number | integer | unique:ture|
| user_id | references | null:false, foreign_key:ture|

### Association

belongs_to :purchase

