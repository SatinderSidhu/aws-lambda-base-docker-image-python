## Setup the virtual envirnment 
```
python3 -m venv .venv 
```
Activate 
```
source .venv/bin/activate
```

Follow the instructions 
https://docs.aws.amazon.com/lambda/latest/dg/python-image.html#python-image-instructions



```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 575527458267.dkr.ecr.us-east-1.amazonaws.com
```
Build Image 
```
docker buildx build --platform linux/arm64 --provenance=false -t mta-eba .
```
After the build completes, tag your image so you can push the image to this repository:
```
docker tag mta-eba:latest 575527458267.dkr.ecr.us-east-1.amazonaws.com/mta-eba:latest
```
Run the following command to push this image to your newly created AWS repository:
```
docker push 575527458267.dkr.ecr.us-east-1.amazonaws.com/mta-eba:latest
```
