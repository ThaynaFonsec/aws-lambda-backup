# Função Lambda 

## Usando a função lambda com código python.

***Para que você possa em um click, dentro da pataforma aws, criar instances EC2.***

> 1° passo

Criar Key pair na aws no serviço de EC2.

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
      "Action": [
        "ec2:RunInstances"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}

```

Permitindo as funções.

> 3° passo

Script em python - componentes da máquina

Variáveis:

- AMI (id da máquina virtual);
- INSTANCE_TYPE (tipo da máquina - free t2.micro);
- KEY_NAME (key pairs criado);
- SUBNET_ID (VPC - subnet);