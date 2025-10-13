---
title: "AWS IAM for Logging"
date: 2025-02-14T09:18:51-08:00
tags:
	- draft
	- public
	- AWS
	- Programming
---

# History
The saying goes that developer documentation is full of lies (the words of the great [xbrianh](https://github.com/xbrianh)). The longer I work with Cloud Platforms the more I realize this is true, and that there are strange inconsistencies within the API.

In the case of AWS, you use IAM policies to allow/disallow access to resources/actions between you internal infrastructure. 
e.g. 
```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Sid": "AllowLambdaInvocation",
        "Effect": "Allow",
        "Action": [
            "lambda:InvokeFunction",
            "lambda:InvokeAsync"
        ],
        "Resource": "arn:aws:lambda:*:*:function:*"
    }]
}
```

For the most part these are manually managed, when you want to use a resource, you have to define the policy that 