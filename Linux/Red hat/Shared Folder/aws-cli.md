# AWS CLI Cheat Sheet

The AWS CLI provides a command-line interface for interacting with various AWS services. This cheat sheet provides commands and options for effective usage of the AWS CLI.

## Configuration

COMMAND | DESCRIPTION
---|---
`aws configure` | Configure AWS CLI with your access key, secret access key, default region, and output format

## Basic Usage

COMMAND | DESCRIPTION
---|---
`aws <service> <command> <options>` | Execute a specific command for a particular AWS service
`aws help` | Display general help information for the AWS CLI
`aws help <command>` | Display help information for a specific AWS CLI command

## Common AWS Services

COMMAND | DESCRIPTION
---|---
`aws ec2 <command>` | Interact with Amazon EC2 instances
`aws s3 <command>` | Manage Amazon S3 buckets and objects
`aws lambda <command>` | Work with AWS Lambda functions
`aws rds <command>` | Manage Amazon RDS databases
`aws ssm <command>` | Use AWS Systems Manager for managing and configuring EC2 instances

## Listing and Describing Resources

COMMAND | DESCRIPTION
---|---
`aws <service> describe-<resource>` | List or describe resources of a specific type for a given service
`aws <service> list-<resources>` | List resources of a specific type for a given service
`aws <service> describe-<resource> --filters Name=<name>,Values=<value>` | Filter and describe resources based on specific criteria

## Creating and Modifying Resources

COMMAND | DESCRIPTION
---|---
`aws <service> create-<resource> --<parameters>` | Create a new resource with the specified parameters
`aws <service> modify-<resource> --<parameters>` | Modify an existing resource with the specified parameters
`aws <service> delete-<resource> --<parameters>` | Delete an existing resource with the specified parameters

## Working with AWS IAM

COMMAND | DESCRIPTION
---|---
`aws iam create-user --user-name <username>` | Create a new IAM user with the specified username
`aws iam create-group --group-name <groupname>` | Create a new IAM group with the specified groupname
`aws iam attach-user-policy --user-name <username> --policy-arn <policyarn>` | Attach an IAM policy to a specific IAM user
`aws iam attach-group-policy --group-name <groupname> --policy-arn <policyarn>` | Attach an IAM policy to a specific IAM group
`aws iam create-access-key --user-name <username>` | Create an access key for an IAM user
`aws iam add-user-to-group --user-name <username> --group-name <groupname>` | Add an IAM user to a specific IAM group

## AWS CLI Output Options

COMMAND | DESCRIPTION
---|---
`--output <format>` | Set the output format for the AWS CLI (e.g., json, table, text)
`--query <query>` | Use JMESPath query to filter and format the output of AWS CLI commands

