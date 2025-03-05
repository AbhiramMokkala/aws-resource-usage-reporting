#!/bin/bash
##########################################
# author:abhiram                         #
# version:v1                             #
# this script reports aws resource usage #
##########################################
set -x
set -e
set -o
# list s3 buckets
echo "print s3 buckets"
aws s3 ls
# list ec2 instances
echo "print ec2 instances"
aws ec2 describe-instances | jq '.Reservations[].Instances[].InstanceId'
# list lambda
echo "print lambda functions"
aws lambda list-functions
# list IAM users
echo "print IAM users"
aws iam list-users

