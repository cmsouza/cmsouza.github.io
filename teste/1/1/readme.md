# Segmentação de Mídia para ECs

## Geração da lista com os hashes
O Google sugere que seja utilizada encriptação SHA256 para adição de dados pessoais ao Google Analytics.

A lista com os dados pode ser apenas arquivos textos com um dado por linha
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

$ echo -n '' > lista.csv
$ cat emails_habilitados|while read line; do echo -n "${random}${line}"|sha256sum; done|awk '{print $1 ";sim"}' >> lista.csv
$ cat emails_nao_habilitados|while read line; do echo -n "${random}${line}"|sha256sum; done|awk '{print $1 ";nao"}' >> lista.csv
```

O resultado é uma lista contendo os hashes e a informação se deve ou não receber a mídia direcionada:
```
$ cat lista.csv
0cc2fd64e417a806fdd4c01c51c63b405f9889cf4a12225752808f1aa979ece6;sim
4fd7005625cebb5bb192ddcd9c3dfb0067720abf259cf249c54ad713afc3f519;sim
c417e563de79db4d5c68ce2969dda1c15a5cf400892d0f102c3576533928f1eb;nao
```

