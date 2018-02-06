---
layout: post
title: "HOWTO: Use a Personal AWS EC2 Instance as an SSH Tunnel"
date: 2017-02-03 08:07:34 -0600
comments: true
categories: general
---
I recently ditched my T1 line because I found a cellular ISP with no data cap. This new provider gives me about 12 times the downstream bandwidth at 30% of the cost of the T1.

The only problem is that it changes my public IP address everytime I restart the router. This would not normally be a problem but I'm a software engineer and frequently need to access remote resources through SSH or otherwise. We use AWS resources at my company and the security groups require a static IP address to allow access.

I could pay for a static IP address at the ISP, but instead I opted to configure a personal SSH tunnel with a static IP address. This gives me greater flexibility because I can use it for other things and it costs less (about $7-10/month, depending on if you leave it running when you're not using it)

This is my HOWTO guide for getting things setup and minimizing costs.

## Overview

1. Create a personal AWS account
2. Create a low-cost EC2 instance
3. Configure AWS CLI for command line `start`, `stop`, `status` automation
4. Tunnel all the things for fun and profit

## Create a personal AWS Account

I won't go into a lot of detail for this step because Amazon has really good documentation [here](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AMS5.0CreatingAnAWSAccount.html). Make sure to [create the EC2 key pair](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AMS5.0CreatingAnEC2KeyPair.html) for your account as well.

## Create a low-cost EC2 instance

Again, AWS has [great documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html). Follow the docs and configure your instance to your personal taste. If, like me, you will only use it for an SSH tunnel, you won't need a lot of resources.

There are several types of AMIs to choose from. I chose a basic Ubuntu `t2.micro` instance with 1GB of RAM. Follow the documentation and be sure to:

* Create an IAM user account (i.e., `ubuntu`)
* Download your keypair file and store it in `~/.ssh/`,
* `chmod 400 ~/.ssh/your-keypair-name.pem` - make the file readonly
* copy/store the access key, and secret keys (strings) somewhere for later use.
* take note of the region-name, you'll need it later.

## Configure AWS CLI

You'll want to install AWS CLI (Command Line Interface) in order to be able to start and stop your tunnel from the command line, without logging into the AWS console in your web browser.

### For MacOS

```bash
brew install awscli
```

### For Debian-Based Linux (i.e. Ubuntu)

```bash
sudo apt-get install awscli
```

If you only use one account from AWS CLI, you can run `aws configure` with no arguments to setup the defaults. However, if you use multiple accounts add the `--profile account_name` switch:

```bash
aws configure --profile personal
```

Here is a good [post on Stack Overflow](https://stackoverflow.com/questions/593334/how-to-use-multiple-aws-accounts-from-the-command-line/34246053#34246053) about multiple AWS CLI accounts.

**Note: Pay attention to the region name. It must match the region name of your EC2 instance.**

**Configure SSH:**

Edit/create `~/.ssh/config` as follows:

```
Host my-aws-tunnel
  User ubuntu
  # replace the hostname below with your EC2 instance hostname
  HostName ec2-35-161-7-236.us-west-2.compute.amazonaws.com
  # replace the keyfile path below with your EC2 instance keypair file
  IdentityFile ~/.ssh/my-ec2-key-pair.pem

# Follow the other confluence docs for host access to different boxes, or ask a Nutrio admin (Ted)
Host stagnat
  HostName ec2-52-21-83-13.compute-1.amazonaws.com
  User ec2-user
  IdentityFile ~/.ssh/staging-vpc-keypair.pem
  ForwardAgent yes
  ProxyCommand ssh my-aws-tunnel -W %h:%p
```
