# Lecture 13 (2-17)

Many applications maintain a dynamic set of elements (or values) where each element is associated with a key from the universe *U*.

Three types of operations can be performed on the dynamic set.

1. The operation $put(k,v)$ inserts a new pair of key $k$ and element $v$ into the dynamic set.
If the set already contains an old pair with the same key, then the old pair is replace by the new pair.
To avoid losing any element, no two elements have same key.

2. The operation $remove(k)$ deletes the pair with given key $k$ from the set and returns its element.
If the set contains no apir with the given key, then the operation returns null.

3. The operation $get(k)$ searches for a pair with the given key $k$ in the set and returns its element.
If the set contains no pair with the given key, the operation returns null.

## Hash tables

The dynamic set is called a dictionary with the three types of dictionary operations called `INSERT`, `DELETE`, and `SEARCH`.

A hash table is an effective data structure for supporting dictionary operations.

A hash table is based on an array `T[0..m-1]`.

If the size of the universe $U$ is much larger than the size $m$ of the array $T$, then a hash function $h$ is used to map a key $k$ into an array index, that is, $0 \leq h(k) \leq m-1$, with $h(k)$ called the hash value of the key $k$.

Because two keys may be mapped to the same array index, a situation called collision, for each array index $j$ with $0 \leq j \leq m-1$, the hash table slot `T[j]` contains a linked list a key-element pairs whose hash vlaue is $j$.
Collisions are resolved with chaining.

## Implementation of the Dictionary Operations

For each index $j$, $0 \leq j \leq m-1$, `T[j]` is null if the list is empty, otherwise it points to the first object in its list.

Each list object contains the key and value attributes and pointers to the next and previous objects.

The next attribute of the last object in the list is null.

```
INITIALIZATION
for j = 0 to m-1
    T[j] = null

// Finds the entry with key k
CHAINED-HASH-FIND(T, k)
    entry = T[h(k)]
    while entry != null
        if entry.key == k
            return entry
        entry = entry.next
    return null

// Inserts a pair of key and value
// at the ehad of the list T[h(k)]
CHAINED-HASH-PUT(T, k, v)
    entry = CHAINED-HASH-FIND(T, k)
    if entry != null
        oldvalue = entry.value
        entry.values = v
        return oldvalue
    note = ALLOCATE-OBJECT()
    node.key = k
    node.value = v
    node.next = T[hv = h(k)]
    if T[hv] != null
        T[hv].prev = node
    T[hv] = node
    node.prev = null

CHAINED-HASH-REMOVE(T, k)
    entry = CHAINED-HASH-FIND(T, k)
    if entry == null
        return null
    if entry.prev != null
        entry.prev.next = entry.next
    else
        T[h(k)] = entry.next
    if entry.next != null
        entry.next.prev = entry.prev
    return entry.value
```

## Analysis of Hashing with Chaining

In the worst case, each operation takes $O(n)$ time.

Below we consider the average case-performance of hashing.

Let $T$ be a hash table with $m$ slots that stores $n$ elements.

Then the load factor $\alpha = n/m$ is the average number of elements stored in a chain under the assumption of simple uniform hashing.

This assumption says that any given element is equally likely to hash into any of the $m$ slots, independently of where any other element has hashed to.

It can be shwoen that the expected length of the list `T[j]` is $\alpha = n/m$.

Assume that the time for computing $h(k)$ is $\Theta(1)$.

Consider the average-case time of an unsuccessful search.

Any key $k$ not already stored in the hash table $T$ is equally likley to hash to any of the $m$ slots.

The search for key $k$ reaches the end of the list `T[h(k)]` of expected length $\alpha$.

The expected number of objects checked in the unsuccessful search is $\alpha$, and the average-case time of the search is $\Theta(1 + \alpha)$.

Similarly, it can be shown that a sucessful search takes $\Theta(1 + \alpha)$ on average.

If $n$ is in $O(m)$, then $\alpha = O(1)$. Thus, `CHAINED-HASH-FIND()` takes $O(1)$ time on average, and each of the three operations takes $O(1)$ time on average.

Note that the textbook `INSERT` and `DELETE` procedures take a list object as input and take $O(1)$ to insert it to or to remove it from the list.

This arrangement is not possible in Java, where a key is needed in both put and get operations.

In practice, hash tables are more efficient than self-balancing binary search trees `BST` (such as Red-Black Tree, AVL Tree, Splay Tree), which take $O(\log n)$ in the worst time.