docker run  --name mongodb -d --rm -p 27017:27017 mongo

cd backend

docker build -t goals-node .

docker run --name goals-backend --rm -d  -p 80:80 goals-node

cd frontend

docker build -t goals-react .

docker run --name goals-frontend --rm -d  -p 3000:3000 -it goals-react

#it react projeleri için gerekiyor

docker network create goals-network

docker run mongo