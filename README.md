# Função Lambda 

## Usando a função lambda com código python.

***Para que você possa realizar backup de instances ec2,
de forma automática.***

> 1° passo

Definir TAG na instance:

- Key : backup
- Value : true

> 2° passo

Função lambda - com script de permissões definindo:

- CloudWatch Logs
- EC2

```
{
  "Version": "2012-10-17",
  "Statement": [{
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "arn:aws:logs:*:*:*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:CreateSnapshot",
        "ec2:CreateTags",
        "ec2:DeleteSnapshot",
        "ec2:Describe*",
        "ec2:ModifySnapshotAttribute",
        "ec2:ResetSnapshotAttribute"
      ],
      "Resource": "*"
    }
  ]
}
```

> 3° passo

Script em python

> 4° passo 

Fazer o agendamento no CloudWatch de quando essa função vai rodar.