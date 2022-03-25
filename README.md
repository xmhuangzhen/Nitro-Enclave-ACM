# Nitro Enclaves ACM demo

This demo shows the AWS Certificate Manager for Nitro Enclaves application.

[AWS Certificate Manager (ACM)](https://aws.amazon.com/certificate-manager/) for Nitro Enclaves allows you to use public and private SSL/TLS certificates with your web applications and web servers running on Amazon EC2 instances with [AWS Nitro Enclaves](https://aws.amazon.com/ec2/nitro/nitro-enclaves/).

The scripts in this demo are based on the following [user guide]( https://docs.aws.amazon.com/enclaves/latest/user/nitro-enclave-refapp.html).

## Prerequisites

Most resources will be provisioned by the AWS CDK script, including the ACM Certificate. However, the Route53 Hosted Zone is not managed with Infrastructure as Code, since it is likely managed and used in other demos and applications as well. Therefore, there needs to be a pre-existing Hosted Zone in your AWS account.

Also, your account needs to be subscribed to the AWS Marketplace AMI called [AWS Certificate Manager for Nitro Enclaves](https://aws.amazon.com/marketplace/server/configuration?productId=3f5ee4f8-1439-4bce-ac57-e794a4ca82f9&ref_=psb_cfg_continue).

## Deployment

To deploy the demo, you need to use the [AWS CDK](https://aws.amazon.com/cdk/).

Installing dependencies:

```sh
pip install -r requirements.txt
```

Deploying:

```sh
cdk deploy --context domain_name=demo.training
```

Note that `demo.training` needs to be replace with the hosted zone name in your account.


### installing steps

```git
sudo yum update -y

export AWS_ACCESS_KEY_ID=xxxxxxxxxxxxxx
export AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxx
export AWS_DEFAULT_REGION=xxxxxxxxxxxxx

sudo yum install git -y

# install npm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
. ~/.nvm/nvm.sh
nvm install node

# install pip
curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py --user
export PATH=~/.local/bin:$PATH

# install cdk
npm install -g aws-cdk

aws sts get-caller-identity
git clone https://github.com/xmhuangzhen/Nitro-Enclave-ACM.git
cd Nitro-Enclave-ACM
pip install -r requirements.txt
cdk bootstrap aws://account_id/account_region --context domain_name=xxxxxxxxxxxxxx
cdk deploy --context domain_name=xxxxxxxxxxxxx
```