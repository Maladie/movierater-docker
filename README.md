# movierater-docker
Docker-compose setup for two java microservices with mongodb and rabbitmq asynchronous communication

Source code available at:

movierater - https://github.com/Maladie/movierater

reviewchecker - https://github.com/Maladie/reviewchecker

# About
Movierater service provides REST endpoints with "HATEOAS-like" navigation. Reviewchecker approves received reviews.
Both applications can be called to check status, respectively on:
  - http://localhost:8081/reviewchecker-0.0.1/hello
  - http://localhost:8080/movierater/hello

# Endpoints
Service entry point is - http://localhost:8080/movierater/movies It provides json with all movies in database and also links to connected resources.

# Curl Examples
- Add new movie (this method also adds new actors and updates rating if movie is already in database)
  - curl -X PUT -H "Content-Type: application/json" -d '{"title": "Wojna domowa", "rating": 2.2, "director": "Kowalski", "actors": [ "Wasiluk", "Filut"] }' http://localhost:8080/movierater/movies
  
- Get movie
  - curl -X GET http://localhost:8080/movierater/movies/{movietitlehere}
 
- Delete movie
  - curl -X DELETE http://localhost:8080/movierater/movies/{movietitlehere}
  
- Send new review to verification
  - curl -X POST -H "Content-Type: application/json" -d '{"author: "Some author", "content": "Some content"}' http://localhost:8080/movierater/movies/{movieTitleHere}/reviews
  
- Get all reviews of given movie
  - curl -X GET http://localhost:8080/movierater/movies/{movietitlehere}/reviews

- Get review of given author, given movie
  - curl -X GET http://localhost:8080/movierater/movies/{movietitlehere}/reviews/{author}
