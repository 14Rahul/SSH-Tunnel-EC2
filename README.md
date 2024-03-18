# SSH-Tunnel-EC2

Create tunneluser with no bash enable

IAM Permission


{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Action": [
                "ssm:StartSession",
                "ssm:TerminateSession"
            ],
            "Resource": [
                "arn:aws:ec2:us-east-2:532968567499:instance/i-021fa8d23587645c9",
                "arn:aws:ssm:*:*:document/AWS-StartSSHSession"
            ]
        },
        {
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "ec2-instance-connect:SendSSHPublicKey",
            "Resource": [
                "arn:aws:ec2:us-east-2:532968567499:instance/i-021fa8d23587645c9"
            ],
            "Condition": {
                "StringEquals": {
                    "ec2:osuser": "tunneluser"
                }
            }
        }
    ]
}
