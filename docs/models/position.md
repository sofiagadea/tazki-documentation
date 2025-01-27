# Position Model

## Description
The `Position` model represents different roles within a company. Each position is associated with a specific enterprise and can have multiple users. 

## Scopes 
- **`search`**: Searches for positions whose name partially matches the provided `query`.

## Validations
- **`name`**: name must be present and unique within the same enterprise.

## Relationships
- **`has_many :users`**: A position can have multiple assigned users.
- **`belongs_to :enterprise`**: A position belongs to a specific enterprise.
- **`has_many :program_registers`**: Relation with associated program registers.
- **`has_many :base_quick_access_positions`**: Relation with base quick access configurations linked to the position.
- **`has_many :position_core_activities`**: Relation with core activities for the position, with cascading deletion.
- **`has_many :core_activities, through: :position_core_activities`**: Indirect relation to core activities. Core activities can be related to one or many positions.

## Public Methods

### **`.active_user_ids`**
Retrieves the IDs of active users associated with the position.

### **`.show_all (class method)`**
Fetches all positions with users and returns their details in a formatted hash.

### **`.to_show`**
Returns a hash of the position's attributes with additional details such as active users, user count, and whether the position is deletable.

## Private Methods
### **`.deletable?`**
Checks if the position can be deleted by verifying the absence of associated core activities, base quick access positions, program registers and users. 

### **`.allow_delete?`**
raise errors before destroying when position is not deletable.