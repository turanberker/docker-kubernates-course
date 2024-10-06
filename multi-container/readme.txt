docker run  --name mongodb -d --rm -p 27017:27017 mongo

cd backend

docker build -t goals-node .

docker run --name goals-backend --rm -d  -p 80:80 goals-node