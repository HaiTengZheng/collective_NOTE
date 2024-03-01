# web framework
```
             --------------------------------------------
             | Business login        ^   User           |
             |                       ^   Implementations|
             |                       ^                  |
             --------------------------------------------
             | Route handler         ^                  |
             | ...                   ^ Warp             |
             |                       ^                  |
             --------------------------------------------
             |                       ^                  | included
             | Tcp stream -> HTTP    ^ Hyper            | in Warp
             |                       ^                  |
             --------------------------------------------
             |                       ^                  | has to be added 
             | Runtime               ^ Tokio            | to the project
             |                       ^                  |
             --------------------------------------------
     | TCP   |-----                  ^                  |
CLOUD| ----> | NIC|   Kernel I/O tasks                  | kernel
     | <---- |-----                                     |
             --------------------------------------------
```
