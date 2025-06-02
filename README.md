//Q1
Intuition
The LRU cache ensures the most recently accessed item is always at the front of a doubly linked list. When the cache exceeds its capacity, the least recently used item (at the end of the list) is removed. This guarantees O(1) operations for both lookup and eviction.

Components
1. Node Class
Represents each entry in the cache.

Contains:

key and value

prev and next pointers for DLL navigation

2. LRUCache Class
Maintains:

capacity: maximum number of items

unordered_map<int, Node*> m: maps keys to DLL nodes

Dummy head and tail nodes to simplify insert/delete logic

 Key Methods
 addNode(Node* newNode)
Inserts a node right after head (most recently used position).

deleteNode(Node* delNode)
Removes a node from its current position in the list.

 put(int key, int value)
If key exists: removes old node and inserts updated one at front.

If key doesn’t exist and capacity is reached: removes the least recently used node (before tail) and inserts new node at front.

Always updates the map accordingly.

get(int key)
If key is found: moves the node to the front (most recently used) and returns its value.

If not found: returns -1.

Time & Space Complexity
Time Complexity: O(1) for both get() and put() operations.

Space Complexity: O(capacity) for storing nodes and map entries.









//Q2
Intuition:
Use an array of buckets with chaining to handle collisions!
Each bucket is a list that stores key-value pairs.

Approach:
Use a fixed-size array of size 10000 to distribute keys.
Apply modulo (key % n) for hashing.
Handle collisions by storing key-value pairs in a vector for each bucket.
Complexity:
Time Complexity:
put: O(k) (k = bucket size)
get: O(k)
remove: O(k)
Space Complexity: O(N) (for N key-value pairs)
