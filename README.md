# Função Lambda 

## Usando a função lambda com código python.

***Para que você possa diminuir o tamanho da imagem após o upload,
de forma automática.***

> 1° passo

Criar o bucket de origem e destino.

> 2° passo

Função lambda - com script de permissões definindo:

- CloudWatch Logs
- S3

```

{
    "Version": "2012-10-17",
    "Statement": [
        {
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
                "s3:GetObject"
            ],
            "Resource": "arn:aws:s3:::adicionar-bucket-origem/*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject"
            ],
            "Resource": "arn:aws:s3:::adicionar-bucket-destino/*"
        }
    ]
}

```

Adicionar o Tigger e definir o bucket de origem.


> 3° passo

Script em python

Importar o biblioteca PIL para dentro da função lambda.

Variável:

- DEST_BUCKET (bucket de destino);