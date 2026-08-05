std::map

std::unordered_map

sorted std::vector

boost::

boost::unordered_flat_map

boost::unordered_node_map
- provides pointer + iterator stability by using heap allocations AND more cache-friendly lookup than unordered_flat_map via SIMD-scanned metadata arrays that the hash lands in instead of a bucket chain thing

boost::concurrent_node_map
- same hashing benefits as ^ but fully multithread safe WITHOUT mutexes or locks, all handled internally via locking specific metadata blocks