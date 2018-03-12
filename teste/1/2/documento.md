![Teste](http://ciro.inie.com.br/public/images/test-logo.png)

> Área - Teste<br />
> Documento de Especificação Técnica

<br />

## Teste de Teste
Última atualização: 12/03/2018 <br />
Em caso de dúvidas, entrar em contato com: [teste@teste.com.br](mailto:teste@teste.com.br)

<br />

## Índice
- [Objetivo](#objetivo)
- [Overview e Descrições Técnicas](#overview-e-descrições-técnicas)
- [Especificação de Micro-conversões](#especificação-de-micro-conversões)
- [Especificação de Conversões](#especificação-de-conversões)
- [Especificação de Conversões - Enhanced Ecommerce](#especificação-de-conversões---enhanced-ecommerce)
- [Considerações Finais](#considerações-finais)

<br />

## Objetivo
Este documento tem como objetivo instruir a implementação do Google Tag Manager, da camada de dados e de dataAttributes para utilização de recursos de monitoramento do Google Analytics referentes ao ambiente de [teste](http://www.testerecarga.com.br/).

<br />

## Overview e Descrições Técnicas

### Google Tag Manager

> É uma ferramenta da Google onde são inseridas pequenas instruções javascript com a finalidade de estruturar a coleta dados e unificar diversos fornecedores de tags terceiros sem a necessidade de várias implementações complexas de hardcode do projeto.

**Instalação**<br />
Para instalar o Google Tag Manager é preciso que o desenvolvedor inclua os códigos abaixo no HTML do site, em todas as páginas do site proposto. Caso o site possua algum template comum que é inserido em todas as páginas, também pode ser utilizado.

Cole o código abaixo após a tag `<head>` do site:

```html
<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start': new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0], j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src='https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);})(window,document,'script','dataLayer','GTYC-2983475H);</script>
<!-- End Google Tag Manager -->
```

Cole o código abaixo, após a tag `<body>` do site:

```html
<!-- Google Tag Manager (noscript) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTYC-09843580934H height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<!-- End Google Tag Manager (noscript) -->
```

