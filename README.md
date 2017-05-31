# Handle-django-cache-redis

Look at the other branch of this code.

### Main packages:
Django (v1.9.8)
Django Debug Toolbar (v1.4)
django-redis (v4.4.3)
Redis (v3.2.0)

### Run redis server by: $ redis-server

### Test CLI whether it connects to redis-server or not: $ redis-cli ping
OUTPUT: PONG

### Modify settings.py to use redis backend for cache. Look for settings.py

### Set CACHE_TTL for TIMEOUT sessions 

You should consider caching the result of a request when the following cases are true:

rendering the page involves a lot of database queries and/or business logic,
the page is visited frequently by your users,
the data is the same for every user,
and the data does not change often.

### https://www.npmjs.com/package/loadtest - Blast the url with requests using loadtest node module
Add loadtest to package.json

### Execute this command in terminal to blast the /cookbook/ url with requests: 
### $ loadtest -n 100 -k  http://localhost:8000/cookbook/

### Look for services.py and views.py for how redis cache backend is used to fetch database related queries
### Look for use of decorators in views.py or the function defined in services.py. Choose either one of them

### Again run: $ loadtest -n 100 -k  http://localhost:8000/cookbook/
### This time more requests per second can be handled.

### Inspecting redis with cli
```
$ redis-cli -n 1
127.0.0.1:6379[1]> keys *
1) "example:1:views.decorators.cache.cache_header"
2) "example:1:views.decorators.cache.cache_page"
127.0.0.1:6379[1]> get "example:1:views.decorators.cache.cache_page"
```

NOTE: Run the flushall command on the Redis CLI to clear all of the keys from the data store. Then, you can run through the steps in this tutorial again without having to wait for the cache to expire.

### Link for tute: https://realpython.com/blog/python/caching-in-django-with-redis/
