# CORS
cross-origin resource sharing
```
user                    Browser                 Server (different.domain.io)
  |                         |                        |
  |  HTTP POST, domain.io   |                        |
  |------------------------>| Preflight request      |       
  |                         | (HTTP OPTIONS)         |
  |                         |----------------------->|
  |                         |                        |
  |                         | Preflight response     |
  |                         | * allowd origin        |
  |                         | * allowd methods       |
  |                         | * allowd header        |
  |                         |<-----------------------|
  |                         |                        |
  |                         | Actual POST request    |                        
  |                         |----------------------->|
  |                         |                        |
  |                         | Actual POST response   |                        
  |                         |<-----------------------|
  | Browser dilivers answer |                        |
  |<------------------------|                        |
  |                         |                        |
```
