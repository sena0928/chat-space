
# CHATSPACEのDB設計

# users_table
- デバイスを使用して作成

|Column|Type|Options|
|------|----|-------|
|name|string|index:true,null:false,unique:true|
|mail|string|null:false,unique:true|

### Association
- has_many :group_users
- has_many :groups,through::group_users
- has_many :messages

# groups_table
|Column|Type|Options|
|------|----|-------|
|name|string|index:true,null:false,unique:true|

### Association
- has_many :group_users
- has_many :users,through::group_users
- has_many :messages


# messages_table
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|group|references|foreign_key: true,null:false|
|user|references|foreign_key: true,null:false|

### Association
- belongs_to :group
- belongs_to :user

# groups_users_table
|Column|Type|Options|
|------|----|-------|
|group|references|foreign_key: true,null:false|
|user|references|foreign_key: true,null:false|

### Association
- belongs_to :group
- belongs_to :user