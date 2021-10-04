# Caching

## Caching profile

Profile defines how data will be evicted from the cache. There are several popular policies:

- LRU (least recently used)
- LFU(least frequently used)

## Type of Cache

This decides how consistent the data in the cache is.

Write Through cache:

- in case of update we first update the cache and then make the modification to the database.
- issues:
  - in case of multiple distributed system this is a problem as we need to update all db.

Write Back Cache:

- in case of update we first update database and evict the data from the cache so that later it can again be populated from the database.
- issues:
  - main big issue is performance as invalidating any record from the cache may degrade the performance.

its suggested to you hybrid kind of policy which works best and we get best of both the worlds.
