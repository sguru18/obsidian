boost::intrusive is pretty cool, removes container bookkeeping

generally just **vector** if **size known** or no key-value relation,
**boost::unordered_flat_map** for **performance** and **scale** basically best map,
**boost::unordered_node_map** if **ownership patterns unclear** (need pointer stability), 
and std::unordered_map only if no stl (ts lowk buns)

![[Screenshot 2026-08-05 at 20.41.39.png]]
^ notice: boost unordered flat map just too goated, boost node map empirically better than unordered map, 

reasons:
vector --> cache locality
boost::unordered_flat_map --> closed hashing means no pointer chasing, SIMD instructions + cache locality to check metadata block means speed, no per-element allocation means speed and less memory. goated data structure really
boost::unordered_node_map --> per element allocation like std but closed hashing (better index layer)


**other breakdown of when to use what**
- if keys are bounded integers, direct vector is always best. else:
- made once, read often --> boost::unordered_flat_map with reserve
- update often, read often --> boost::unordered_flat_map (rehash spikes), avoid with boost::unordered_node_map
- need sorted order
	- made once --> sorted vector (boost::flat_map)
	- update often --> std::map iff other designs don't work
- small --> sorted vector
- heavy multithreading --> boost::concurrent_node_map or sharded container

std::map
- ordered, implemented as a red black tree
- lookup and insert is O(log(N)), sorted order for free
- if one time construction
	- sorted vector approach better, binary search more cache efficient there for lookup
- else if frequently updated but don't need sorted:
	- boost::unordered_flat_map with reserve
- if frequently updated and need sorted order
	- this is best but last resort. opt for unordered_flat_map and sort when needed

std::unordered_map
- standard O(1) lookup and insert hashmap, but not performant at scale for insert or lookup because of separate chaining (hash gives you a bucket, follow bucket to a node, maybe next node...)

boost::flat_map
- built on top of a sorted vector, great lookup and excellent iteration
- read-optimized structure, good for one-time construction and frequent iteration

boost::unordered_flat_map
-  more cache-friendly lookup than unordered_map via closed hashing: SIMD-scanned metadata arrays that the hash lands in instead of a bucket chain (open hashing)
- useful for efficient construct --> lookup many times --> throw away, not long term. ie. per message processing
- requires moving items during rehash which means pointer invalidation, avoid this by using reserve

boost::unordered_node_map
- same principles as ^ but provides pointer + iterator stability by using heap allocations 
- then you use map[idx].get() instead of &map[idx]

boost::concurrent_node_map
- same hashing benefits as ^ but fully multithread safe WITHOUT mutexes or locks, all handled internally via locking specific metadata blocks

practically probably better to design threads to not mutate shared data, own their data and reconcile in between steps or something