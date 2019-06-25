# ghost on elastic beanstalk

This repo represents that you will need in order to setup an ghost instance on elastic beanstalk.

Fork this repo and modify for your requirement. 


Once you setup the ghost environment, add the following environment variables. 

- database__client: mysql
- database__connection__host: db
- database__connection__user: root
- database__connection__password: example
- database__connection__database: ghost
- url: https://myblog.com
- S3_ASSET_BUCKET: bucketname

Setup the database accordingly


Beanstalk requires permission to the s3 bucket for asset syncing.

Sample policy json for s3 bucket.
```
{
    "Version": "2008-10-17",
    "Statement": [
        {
            "Sid": "beanstalk",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::1234567890:role/aws-elasticbeanstalk-ec2-role"
            },
            "Action": [
                "s3:Get*",
                "s3:List*",
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::bucketname/*",
                "arn:aws:s3:::bucketname"
            ]
        }
    ]
}
```






