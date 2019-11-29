
# CHATSPACEのDB設計

# users_table
- デバイスを使用して作成

|Column|Type|Options|
|------|----|-------|
|name|string|index:true,null:false,unique:true|
|mail|string|null:false,unique:true|

### Association
- has_many :group_users
- has_many :group,through::group_users
- has_many :messages

# groups_table
|Column|Type|Options|
|------|----|-------|
|name|string|index:true,null:false,unique:true|

### Association
- has_many :group_user
- has_many :user,through::group_users
- has_many :messages


# messages_table
|Column|Type|Options|
|------|----|-------|
|body|text|null:false|
|image|string|
|group|references|foreign_key: true|
|user|references|foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

# groups_users_table
|Column|Type|Options|
|------|----|-------|
|group|references|index: true, foreign_key: true,null:false|
|user|references|null: true, foreign_key: true,null:false|

### Association
- belongs_to :group
- belongs_to :user