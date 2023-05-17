### Delete data from the database

bool delete(string $from [, string $where [, string $fields]])

* **$from** - table in which you want to delete data
* **$where** - condition under which it is necessary to delete data
* **$fields** - list of fields that you want to delete. if not specified the entire row is deleted

***

#### Example

Deleting a user from the database by ID  
```
global $modx, $table_prefix;  
$id = $modx->db->escape($id);  
$modx->db->delete($table_prefix.".modx_web_users", "id = $id");
```
