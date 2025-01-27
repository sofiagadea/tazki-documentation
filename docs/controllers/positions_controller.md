# Position Controller

The Position Controller manages all operations related to positions within an enterprise. Access to these methods is restricted to administrators with specific permissions.

## Methods

### **Index Positions**
- **URL**: `/positions`
- **Method**: `GET`
- **Description**: Fetches a list of positions for the current user's enterprise. Supports filtering and pagination.
- **Headers**:
  - `filters`: A comma-separated list of filters.
- **Parameters**:
  - `search`: A query string to filter positions by name.
  - `limit`: Maximum number of records to return.
  - `offset`: Number of records to skip.
- **Output**:
  - `info`: The positions information.
  - `filter [related_names]`: List of positions name used for filtering.

### **Transfer Positions**
- **URL**: `/positions/transfer`  
- **Method**: `GET`
- **Description**: Transfers a user position from one position to another within the same enterprise.
- **Parameters**:
  - `user_id`: The user id whose position is trying to be changed.
  - `position_id`: The new position id to which is trying to change.


### **Position Policy**
Defines access rules for the Position model operations. All policies ensure that the user has administrative privileges and does not have specific restricted permissions.
**index**: 
 - User is an admin.
 - User's permissions do not include `Cargos`.

**create?**: 
 - User is an admin.
 - User's permissions do not include `c_position`.

**update?**: 
 - User is an admin.
 - User's permissions do not include `e_position`.

**destroy?**: 
 - User is an admin.
 - User's permissions do not include `d_position`.

**transfer?**: 
 - User is an admin.
 - The position belongs to the same enterprise as the user.