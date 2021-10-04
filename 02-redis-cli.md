# Redis CLI

```sh
# Start redis cli
redis-cli
```

> NOTE: using commands in capital is convention in Redis. However, its case insensitive.

```sh
# Check that redis server is working fine
PING # OUTPUT PONG


# Print Hello World
ECHO "Hello World" # OUTPUT: Hello World

# Close the connection
QUIT
```

Playing with data mainly string

```sh
# set a variable
SET foo 100 # OUTPUT OK
SET bar "Hello World" # OUTPUT OK
SET employee:firstName abhishek # OUTPUT OK
SET employee:lastname das # OUTPUT OK

# set multiple variable
MSET a 10 b 20 c 30

# fetch a variable
GET foo # OUTPUT "100"
GET c # OUTPUT "30"

# increment a value
INCR foo # OUTPUT (integer) 101
# decrement a value
DECR foo # OUTPUT (integer) 100
# kind of concatenation
APPEND bar " , how are you" # GET bar wil return "Hello World , how are you"

# check a variable exists
EXISTS foo # (integer) 1
EXISTS fooo # (integer) 0

# rename a variable
RENAME foo fooo # GET foo will return (integer) 0

# delete a variable
DEL bar # OUTPUT (integer) 0

# getting undefined value
GET bar # OUTPUT (nil)

# set lifetime or expiry of a variable
EXPIRE greeting 50 # will expire in 50 seconds
# check the life of a variable
TTL greeting # positive value indicates variable will expire in that much sec, -1 indicates expiry is not set, -2 indicate variable already expired
# set and configure expiry at same time
SETEX this_will_expire 50 "hello world"
# persists something which was configure to expire
PERSIST this_will_expire # TTL of this will not return -1

# Delete everything from REDIS
FLUSHALL
```

List and its operation. List are always list of string sorted in insertion order.

```sh
# Creates a list if not present
LPUSH people "Bob" # push at front of the list
LPUSH people "Tom" # push at front of the list
LPUSH people "Dom" # push at front of the list

# fetch a list
LRANAGE people 0 -1
# OUTPUT
## 1) "Dom"
## 2) "Tom"
## 3) "Bob"
LRANAGE people 1 2
# OUTPUT
## 2) "Tom"
## 3) "Bob"

RPUSH people "Abhishek" # push at last of list

# length of the list
LLEN people # OUTPUT: 4

# many other command are available
LPOP RPOP LINSERT
```

Sets

```sh
# create a set
SADD cars "Ford"
SADD cars "BMW"

# print the set
SMEMBERS cars

# delete a element from the set
SREM cars "BMW"

# how many element are there in the set
SCARD cars

# check if exists in set
SISMEMBER cars "BMW" # if there return 1, else 0

# many other command are available
SMOVE
```

sorted sets, the difference is every member is associated with a score(integer). That score is used to sort a set.

```sh
# create a sorted set
ZADD users 1991 "abhi" # 1991 is used for sort
ZADD users 1990 "suta" 
ZADD uses 1992 "lala"

# print everything
ZRANGE users 0 -1

# get the position of any element
ZRANK users "abhi" # 1

#etc etc
```

it goes on for all the data types... redis have a very extensive documentation.
