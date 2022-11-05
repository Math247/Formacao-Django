# O que é HTTP?
Quando se fala em HTTP pensamos primeiramente em internet. No momento em que acessamos o curso na Alura, aconteceu uma comunicação entre o navegador e a Alura. Essa comunicação se chama Client-Server. É um modelo arquitetural, então a internet inteira é baseada nisso onde há um cliente que solicita e um servidor que responde.

**E em qualquer comunicação é necessário regras. Esse conjunto de regras é basicamente um protocolo, onde nesse cenário é o HTTP.**

# HTTPS - A versão segura do HTTP:
Quando usamos o HTTP, todos os dados enviados entre cliente e servidor são transmitidos em texto puro, inclusive dados sensíveis como login e senha. Quando o navegador pede essas informações, há varios intermediários. Usando uma conexão Wi-Fi, os dados passam para o roteador, depois pro modem do provedor, do modem pra algum servidor do provedor de internet, e mais, antes que os dados realmente cheguem no servidor destino. Mas quando usamos HTTP, qualquer servidor no meio desse processo pode espionar os dados enviados, ou seja, super inseguro. Então, existe o HTTPS, que é basicamente o HTTP comum, porém mais seguro.

# Funcionamento do HTTPS:
O HTTPS para garantir a segurança usa criptografia baseada em chaves públicas e privadas. Para gerar essas chaves, é preciso  garantir a identidade de quem possui essas chaves e é feito a partir de um certificado digital. Além disso, uma autoridade certificadora, um órgão ou entidade confiável, deve garantir não apenas a identidade do site mas a validade do certificado.
Assim, os navegadores com a chave pública criptografam as informações e as enviam pro servidor que as descriptografa com a chave privada.

# Endereços sob seu domínio:
https://www.alura.com.br -> Já sabemos sobre o https. Logo depois, vem o nome do site, www.alura.com.br. No vocabulário de um desenvolvedor isso é o domínio. O "br" indica um site do Brasil. Ele representa o top level domain. Depois vem o "com" abreviação de "comercial", e por fim "alura". O "com" e "alura" são sub-domínios.

# Subdomínios:
O gmail temos o endereço: mail.google.com , o drive é drive.google.com. Os dois são subdominios do dominio Google. Eles apontam pra páginas diferentes dentro do mesmo dominio (Google)

# Endereços IP's:
O dominio basicamente é o nome do site na internet para ser fácil de se lembrar. Na verdade, a internet funciona sem esses domínios. Os nomes são para gente, para a máquina na internet, tem outra forma de se endereçar. Elas usam o endereço IP, que são números díficeis de decorar. Sendo assim conseguimos acessar Google apenas com o IP.

# DNS:
Mas a gente não acessa nenhum site pelo por um número, e sim pela URL. Seria inviavel decorar todos esses números. Acontece que por baixo dos panos quando escrevemos e realizamos uma requisição, essa URL é transformada em número por um serviço chamado DNS (Domain Name System). Ele age como um banco de dados de domínio. Assim, quando fazemos uma requisição para alura.com.br, o DNS age transformando para um IP e a requisição continua.

# Portas:
Existem portas reservadas para cada protocolo. A porta para o HTTP é a 80. Não precisamos colocar isso no browser, mas se quisermos ficaria assim: http://www.alura.com.br:80 . Vai funcionar normalmente. Mas se colocarmos 81 por exemplo. Não funciona pois essa porta não está aberta no servidor. O protocolo HTTPS tem como porta padrão a porta 443. Testando ficaria assim: https://www.alura.com.br:443

# Recursos:
https://alura.com.br/dashboard. O /dashboard é um recurso do site que gostaríamos de acessar. Existem vários recursos dentro da Alura.

# Finalmente, a URL:
Todos os endereços web seguem esse mesmo padrão: "protocolo://dominio:porta/recurso. Ele segue uma especificação que foi batizada de Uniform Resource Locator abreviada como URL. Então URL's são os endereços na web!

# Modelo Requisição e Resposta:
No mundo HTTP a requisição enviada pelo navegador para o servidor é chamada de HTTP REQUEST. Recebemos uma página, por exemplo, /dashboard como resposta, já que enviamos login e senha validos no login da alura. Essa resposta é chamada de HTTP RESPONSE. A comunicação segue esse modelo, o cliente envia uma requisição e o servidor responde.
Agora se formos no globo.com e clicarmos em algum artigo do site, percebemos que TODA a pagina foi troca. A ideia do HTTP é justamente essa, cada recurso é independente um do outro. Isso se aplica também pros dados enviados na requisição. Cada reequisição é independente da outra.
Essa caracteristica de que cada requisição é independente da outra é chamada de stateless. Isso significa que o HTTP não há como lembrar das requisições anteriores enviadas para o servidor. Por isso precisamos incluir em cada requisição todas as informações sempre.

# Sessões:
Porém fazendo login da alura e termos enviado varias requisições eu continuo logado. Ou seja, a Alura de alguma forma lembra que eu fiz login em alguma requisição anterior. Como falamos, cada requisição deve enviar todas as informações para gerar uma resposta. Isso significa que o navegador envia em cada requisição informações sobre o meu usuário.
Então o navegador envia o login e senha em cada requisição? Não. Mas faz algo parecido. Quando efetuamos o login, a alura valida os dados. Nesse momento, o servidor tem certeza que o usuario existe e gera uma identificação quase aleatoria para o usuario. Essa identificação é um numero criado ao vivo e muito dificil de advinhar. Esse numero é a identificação temporaria do usuario e ele sera devolvido em resposta.

# Cookies:
Então onde esta esse numero? O navegador grava esse numero em um arquivo especial, são os famosos cookies. Todas as plataformas ajudam a gerar esse numero e a criar o cookie de maneira transparente. É dessa forma que as plataformas gerenciam as SESSÕES com o usuário. No resumo, o HTTP usa sessões para salvar informações de usuario. Sessões só são possiveis por uso de Cookies. Cookies são pequenos arquivos que guardam informações no navegador. HTTP é stateless, não mantem estado.

# Depurando a requisição HTTP:
Erro 404 quer dizer que o servidor não encontro o recurso (Not Found)
Quando acontece um problema no servidor, o codigo mais comum eh o 500.
São muitos codigos, mas o importante saber é:
Começa com 2xx -> Coisa Boa
Começa com 3xx -> Significa normalmente que o navegador precisa fazer algo a mais (o cliente precisa agir) pois algo mudou ou um recurso não existe mais.
Começa com 4xx -> Significa que o navegador enviou dados errados, como uma URL errada.
Começa com 5xx -> Servidor gerou algum problema.

# Parametros da requisição:
Acessar youtube.com  e pesquisar Ayrton Senna. Quando pesquisamos a URL mudou. O recurso acessado, que se chama "results" tem parametros da requisição indicados pela "?":
https://www.youtube.com/results?search_query=Ayrton+Senna
O parametro se chama search_query. O HTTP permite enviar mais de um parametro, basta concatenar o prox parametro com o caractere "&"
No console aparece o tipo da requisição, sendo GET. O GET envia os parametros pela URL. Isso eh util quando queremos deixar os parametros visiveis. Mas sera que eh bom com login e senha?
Quando mexemos com senha, o metodo HTTP muda. Usamos o HTTP POST. Usando o POST, o navegador envia os dados no corpo da requisição, e não na URL.
O metodo POST foi pensado para criar algo novo no servidos. Ao enviar uma requisição POST para o servidor, nossa intenção é criar algo novo.

# REST:
* GET - Listagem
* Post - Criação
* Put - Atualizar
* Delete - Remover
**Rest -> Tres componentes -> Recurso (URI) -> Operações (GET/POST/PUT/DELETE) -> Representação(JSON/XML/HTML)**

#        Recurso:
Ao criar as URIs do nosso sistema devemos levar em conta que elas representam recursos, não ações. Em sistemas REST, nossas URIs devem conter apenas substantivos, que são nossos recursos: /restaurante/adiciona não é uma boa URI, pois contém um verbo e não está identificando um recurso, mas sim uma operação.
As semânticas principais são:
* GET - recupera informações sobre o recurso identificado pela URI. Ex: listar restaurante, visualizar o restaurante 1. Uma requisição GET não deve modificar nenhum recurso do seu sistema, ou seja, não deve ter nenhum efeito colateral, você apenas recupera informações do sistema.
* POST - adiciona informações usando o recurso da URI passada. Ex: adicionar um restaurante. Pode adicionar informações a um recurso ou criar um novo recurso.
* PUT - adiciona (ou modifica) um recurso na URI passada. Ex: atualizar um restaurante.
* DELETE - remove o recurso representado pela URI passada. Ex: remover um restaurante.

Representação:

Quando fazemos uma aplicação não trafegamos um recurso pela rede, apenas uma representação dele. E essa representação pode ser feita de diferentes formas como JSON, XML ou HTML.
