# cache_coherence_simulation
> This simulation represents how the cache performs to maintain the coherence between two processors using the MSI protocol.
This simulation was performed using SMPCache which is a trace-driven simulator for the analysis and teaching of cache memory systems on symmetric multiprocessors.

### the transition diagram for the MSI protocol

> The basic MSI protocol with the ``Modified``, ``Shared``and ``Invalid`` state
![image](https://user-images.githubusercontent.com/113125527/218504967-3afdf9e9-509f-472e-8563-8854e8c96295.png)
------

# Results *for the first six times of execution*

### *Accesses number 1*

![image](https://user-images.githubusercontent.com/113125527/218723858-10035615-d6d6-4888-93ff-f880b38b7815.png)


As we can see, p0 sent a read request because it wanted to read block 273.
first it searched in its cache and didn't find the data so it showed a miss in cache, then it sent a read request on the bus and the bus response with the data from the main memory.

### *p0 and p1 caches*
![image](https://user-images.githubusercontent.com/113125527/218720473-cd696ad8-cc20-4984-8208-d9a09f9d6165.png)

the state for p0 became shared


### *State Transition*

![image](https://user-images.githubusercontent.com/113125527/218522167-b98926ca-7635-4503-8cb6-074ec680e8eb.png)
> ##### From ``invalid`` to ``shared``

------

### *Accesses number 2*
![image](https://user-images.githubusercontent.com/113125527/218524547-6c85eac3-24b8-4df8-a16b-41da35766f60.png)


p0 sent a read request because it wanted to read block 273.
first it searched in its cache and found the data so it showed ``a hit in cache``.

### *p0 and p1 caches*
![image](https://user-images.githubusercontent.com/113125527/218721889-a7df51dd-a82c-4e8b-81f1-f06e84ca27a8.png)

the state for both p0 and p1 became shared.

### *State Transition*

![image](https://user-images.githubusercontent.com/113125527/218525033-e8aaa731-eeb5-4eeb-a7a7-58d6fb9c65d4.png)
> ##### From ``invalid`` to ``shared`` 
> and now the block is shared for both po and p1

------

### *Accesses number 3*
![image](https://user-images.githubusercontent.com/113125527/218525993-1de5ecd1-7648-47ef-bef2-0a3d12334a8e.png)

 
p0 sent a read request because it wanted to read block 273.
first it searched in its cache and found the data so it showed a hit in cache
 
### *p0 and p1 caches*
![image](https://user-images.githubusercontent.com/113125527/218722279-93e66f88-d923-474f-a19e-9e5945668d49.png)
 
p1 modified the block so it became invalid for p0

### *State Transition*
![image](https://user-images.githubusercontent.com/113125527/218526459-831841c5-8155-4b8a-8921-b9ed6b63aa3d.png)

------

### *Accesses number 4*
![image](https://user-images.githubusercontent.com/113125527/218724419-38f95f29-4106-4647-890a-d37502d024ed.png)

 
in access number 3 p1 modified the block so it became invalid for p0 that explained why it's no longer in p0 cache.
p0 sent a read request ro the bus and the bus reponse with block transfered from p1. 
 
### *p0 and p1 caches*
![image](https://user-images.githubusercontent.com/113125527/218724652-22bc0d0d-6bfc-45dc-a95b-116ce0bbe000.png)
> ``shared`` for both processors.
### *State Transition*

![image](https://user-images.githubusercontent.com/113125527/218724810-df2645a3-5656-41fb-933c-a13acfd98b1b.png)
> p0 state from ``invalid`` to ``shared``
------

### *Accesses number 5*
![image](https://user-images.githubusercontent.com/113125527/218726964-cd9e16d4-0dea-4a26-8842-2c18c2d4bfde.png)

 
p0 found the block in its cache ---> cache hit
 
### *p0 and p1 caches*
![image](https://user-images.githubusercontent.com/113125527/218727548-098deddf-9855-4b84-a859-5bb2098074ca.png)

### *State Transition*
![image](https://user-images.githubusercontent.com/113125527/218727091-053821a7-0085-43cd-83ac-32d1b26f46ea.png)

>``shared`` to ``shared``

------

### *Accesses number 6*
![image](https://user-images.githubusercontent.com/113125527/218727860-d2ebbed3-93cf-44a5-b542-ac419f27223b.png)

 
first p0 found the block in its cache ---> cache hit
then p0 modified it
 
### *p0 and p1 caches*
![image](https://user-images.githubusercontent.com/113125527/218728056-bdc0336b-d381-4892-8b7a-1e3eeda32c24.png)

### *State Transition*
![image](https://user-images.githubusercontent.com/113125527/218728126-6b0acd62-f601-4e10-b9a4-b9d03423c3f6.png)
> from ``shared`` to ``modified``
