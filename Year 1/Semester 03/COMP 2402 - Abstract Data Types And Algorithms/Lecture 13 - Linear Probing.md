**Linear probing** is a collision resolution technique used in **open addressing hash tables**. When a collision occurs (i.e., two keys hash to the same index), linear probing searches the hash table **sequentially (linearly)** for the next available slot.

- **Hash function**: Computes an index for a key, usually with `index = hash(key) % table_size`
- **Collision**: Occurs when two keys map to the same index.
- **Linear probing**: If the calculated index is occupied, probe the next slot `(index + 1) % table_size`, then `(index + 2) % table_size`, etc., until an empty slot is found.


**Notes :**
- **Clustering**: One drawback of linear probing is **primary clustering** — groups of occupied slots form, increasing search time.
- Alternatives: **Quadratic probing** or **double hashing** can help reduce clustering.