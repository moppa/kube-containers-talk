npx create-next-app@latest demo

https://github.com/vercel/next.js/tree/canary/examples/with-docker#in-existing-projects
next.config.js 
  output: 'standalone',

yarn install
yarn dev

docker buildx build -t d-2 .

docker buildx bake

docker compose up
docker compose up -d
docker compose down

export TAG=mytag
export REGISTRY=my.registry.com/
echo -e "TAG: $TAG \nREGISTRY: $REGISTRY"


unset TAG && unset REGISTRY

docker buildx bake


docker push my.registry.com/demo:mytag 