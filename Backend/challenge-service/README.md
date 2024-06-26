*If not use docker compose use below methods.*

# Run

1. `go mod init backend/challenge-service`
2. `go get .`
3. `go run .`

# Docker run

1. `docker build --tag challenge-service .`
2. `docker run --publish 8081:8081 challenge-service`

# Test

### 1. Create Challenge

curl -X POST \
  http://localhost:8081/challenge/create \
  -H "Content-Type: multipart/form-data" \
  -F "testcase=@/home/manuja/DisProject/ProblemSolvingPlatform/Backend/challenge-service/testfiles/testcase.zip" \
  -F "template=@/home/manuja/DisProject/ProblemSolvingPlatform/Backend/challenge-service/testfiles/template.zip" \
  -F "readme=@/home/manuja/DisProject/ProblemSolvingPlatform/Backend/challenge-service/testfiles/readme.md" \
  -F "id=2" \
  -F "title=Example Challenge 2" \
  -F "difficulty=easy" \
  -F "authorid=1234" 

### 2. Get Challenges

curl -X GET http://localhost:8081/challenge/challenges

### 3. Get Challenge By ID

curl -X GET http://localhost:8081/challenge/1

### 4. Get Challenge By Difficulty

curl -X GET http://localhost:8081/challenge/difficulty/easy

### 5. Update Challenge

curl -X PUT http://localhost:8081/challenge/update/3 \
  -H "Content-Type: multipart/form-data" \
  -F "testcase=@/home/manuja/DisProject/ProblemSolvingPlatform/Backend/challenge-service/testfiles/testcase.zip" \
  -F "template=@/home/manuja/DisProject/ProblemSolvingPlatform/Backend/challenge-service/testfiles/template.zip" \
  -F "readme=@/home/manuja/DisProject/ProblemSolvingPlatform/Backend/challenge-service/testfiles/readme.md" \
  -F "title=Changed Challenge Title" \
  -F "difficulty=Medium" \
  -F "authorid=1235"

### 6. Delete Challenge

curl -X DELETE \
  http://localhost:8081/challenge/delete/1

