# Ark
sometimes | something | simple memory 



## The First

## JVM 

### Oracle Docs

- java
  - https://docs.oracle.com/en/
  - https://docs.oracle.com/en/java/javase
  - gctuning: https://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/
    - G1 tuning : https://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/g1_gc_tuning.html#g1_gc_tuning
  - gctuning: https://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/
  
  
#### Humongous Objects and Humongous Allocations

1. Base On JDK8

尝试调整 Region 的大小，`-XX:G1HeapRegionSize`

```
For G1 GC, any object that is more than half a region size is considered a humongous object. Such an object is allocated directly in the old generation into humongous regions. These humongous regions are a contiguous set of regions. StartsHumongous marks the start of the contiguous set and ContinuesHumongous marks the continuation of the set.

Before allocating any humongous region, the marking threshold is checked, initiating a concurrent cycle, if necessary.

Dead humongous objects are freed at the end of the marking cycle during the cleanup phase and also during a full garbage collection cycle.

To reduce copying overhead, the humongous objects are not included in any evacuation pause. A full garbage collection cycle compacts humongous objects in place.

Because each individual set of StartsHumongous and ContinuesHumongous regions contains just one humongous object, the space between the end of the humongous object and the end of the last region spanned by the object is unused. For objects that are just slightly larger than a multiple of the heap region size, this unused space can cause the heap to become fragmented.

If you see back-to-back concurrent cycles initiated due to humongous allocations and if such allocations are fragmenting your old generation, then increase the value of -XX:G1HeapRegionSize such that previous humongous objects are no longer humongous and will follow the regular allocation path.
```





