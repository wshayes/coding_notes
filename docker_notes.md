
# Docker Notes

## AWS

# Login to AWS ECR in Docker for Wm Hayes/us-east-1 account/region
# Retrieve an authentication token and authenticate your Docker client to your registry.
# Note: If you receive an error using the AWS CLI, make sure that you have the latest version of the AWS CLI and Docker installed.
# Use the AWS CLI:

aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 965028819973.dkr.ecr.us-east-1.amazonaws.com

# For wagsites
# Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here . You can skip this step if your image is already built:

docker build -t wagsites .

# After the build completes, tag your image so you can push the image to this repository:

docker tag wagsites:latest 965028819973.dkr.ecr.us-east-1.amazonaws.com/wagsites:latest

# Run the following command to push this image to your newly created AWS repository:

docker push 965028819973.dkr.ecr.us-east-1.amazonaws.com/wagsites:latest

# For appsfolio
docker build -t appsfolio .
docker tag appsfolio:latest 965028819973.dkr.ecr.us-east-1.amazonaws.com/appsfolio:latest
docker push 965028819973.dkr.ecr.us-east-1.amazonaws.com/appsfolio:latest