<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/log-group-cleaner/blob/master/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

# CloudWatch Log Group Cleaner CloudFormation Blueprint

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

This blueprint provisions a [Lambda Function](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-function.html) that periodically cleans up unwanted CloudWatch Log Groups.

* By default, it runs once a day via [CloudWatch Event Rule](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-events-rule.html). This can be configured with
* It includes necessary Lambda Permission and IAM Role
* Optionally supports [VpcConfig](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-function.html#cfn-lambda-function-vpcconfig). Variables can be used to set different values for multiple environments.
* Supports [Lambda X-Ray tracing](https://docs.aws.amazon.com/lambda/latest/dg/lambda-x-ray.html)
* Can customize [ScheduledExpression](https://docs.aws.amazon.com/eventbridge/latest/userguide/scheduled-events.html) or [EventPattern](https://docs.aws.amazon.com/eventbridge/latest/userguide/aws-events.html).

## Usage

1. Add blueprint to Gemfile
2. Configure: configs/log-group-cleaner values
3. Deploy blueprint

## Add

Add the blueprint to your lono project's `Gemfile`.

```ruby
gem "log-group-cleaner", git: "git@github.com:boltopspro/log-group-cleaner.git"
```

## Configure

Use the [lono seed](https://lono.cloud/reference/lono-seed/) command to generate a starter config params files.

    lono seed log-group-cleaner

The files in `config/log-group-cleaner` folder will look something like this:

    configs/log-group-cleaner/
    └── variables
        └── development.rb

Configure the `configs/log-group-cleaner/variables` files if you want to change any of the settings. The defaults should be fine though.

## Deploy

Use the [lono cfn deploy](http://lono.cloud/reference/lono-cfn-deploy/) command to deploy.

    lono cfn deploy log-group-cleaner --sure

## Configure Details

Refer to the [lono lambda extension](https://github.com/boltopspro-docs/lambda_extension) for details on how to configure the Schedule Expression, VPC, X-Ray Tracing, etc.
