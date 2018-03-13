![Zoly](http://lucida-brasil.github.io/public/Images/zoly-logo.png)

Área - Digital Analytics

# Alelo Desenvolve - Segmentação de Mídia para ECs

Última atualização: 13/03/2018

## Objetivo
Criar uma lista de hashes de e-mails e CNPJs de clientes Alelo para segmentar a entrega de mídia digital.

## Implementação
### Geração da lista
O Google sugere que seja utilizada encriptação SHA256 para adição de dados pessoais ao Google Analytics.

A lista com os dados pode ser apenas um arquivo texto contendo um dado por linha
```
$ cat emails_habilitados
ciro.souza@zoly.com.br
teste@teste.com.br
$ cat emails_nao_habilitados
teste2@teste.com.br
```

Uma das formas de encriptar a lista é a seguinte:
```
$ random='d3b1aba48527dd599db0e86f5ad97120'

$ echo -n '' > lista_emails.csv
$ cat emails_habilitados|while read line; do echo -n "${random}${line}"|sha256sum; done|awk '{print $1 ";sim"}' >> lista_emails.csv
$ cat emails_nao_habilitados|while read line; do echo -n "${random}${line}"|sha256sum; done|awk '{print $1 ";nao"}' >> lista_emails.csv
```

### Resultado
A lista contendo os hashes e a informação se deve ou não receber a mídia direcionada é criada:
```
$ cat lista_emails.csv
0cc2fd64e417a806fdd4c01c51c63b405f9889cf4a12225752808f1aa979ece6;sim
4fd7005625cebb5bb192ddcd9c3dfb0067720abf259cf249c54ad713afc3f519;sim
c417e563de79db4d5c68ce2969dda1c15a5cf400892d0f102c3576533928f1eb;nao
```

