# 빌드시 GC 에러날 때 

* error message
~~~
allocation failure GC in old space requested

FATAL ERROR: CALL_AND_RETRY_LAST Allocation failed - JavaScript heap out of memory
 1: node_module_register
 2: v8::internal::FatalProcessOutOfMemory
 3: v8::internal::FatalProcessOutOfMemory
 4: v8::internal::Factory::NewFillerObject
 5: v8::internal::MemoryReducer::TearDown
 6: 000001B234F847A1
~~~

* solution (your javascript file setting)
~~~
node --max_old_space_size=8000 build.js
~~~
