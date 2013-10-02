##1 - Descrição do Produto

O Sistema de Ouvidoria foi desenvolvido em plataforma livre e possibilitará que um cidadão, externo à organização ou empregado desta, submeta mensagens (denúncias, reclamações, críticas, sugestões) para análise e resposta da Ouvidoria da instituição. Isto permitirá que se mantenha aberto um canal de comunicação entre o cidadão e a instituição, auxiliando na identificação de problemas da organização. Através deste sistema a Ouvidoria da instituição poderá efetuar o diagnóstico e a análise dos acionamentos submetidos, visando a rápida solução de questionamentos. Será permitido ao cidadão acompanhar o andamento de seu acionamento através da internet ou de serviço de atendimento da Ouvidoria.

O sistema permitirá a emissão de relatórios gerenciais, apresentando estatísticas dos dados consolidados, visando não só possibilitar melhorias no processo de atendimento da ouvidoria como, também, facilitar o diagnóstico dos problemas nos processos da organização. A área estratégica da Ouvidoria poderá acompanhar todo o processo de atendimento a um acionamento, podendo inclusive agir no processo de solução. O Sistema poderá ser utilizado por Organizações com estrutura orgânica compostas de vários órgãos ou por um único órgão.

##2 - Pré-requisitos

* MySQLServer 4.1.20 instalado;
* MySQL Administrator instalado;
* Tomcat 5.0.28 instalado<b> ¹</b>;
* Java 1.4.2;
* Eclipse 3.6 ou superior instalado<b> ¹</b>;
* Browser Firefox 3.0 ou superior<b> ²</b>.
* Maven 2<b> ³</b>.

	<b>¹.</b> A codificação padrão da aplicação deve ser “UTF-8”, esteja ela rodando dentro do Eclipse ou direto no servidor.<br>
	<b>².</b> Garantimos o correto funcionamento da aplicação neste browser. Para utilização de outros navegadores, deverão ser realizados testes para garantir a compatibilidade.<br>
	<b>³.</b> O Maven é o responsável por manter as dependências de bibliotecas utilizadas pelo software.

<b>O software foi testado utilizando estas versões. A utilização de versões diferentes pode ocasionar erros.
Caso você seja um usuário iniciante, sugerimos que você use o <i>framework Demoiselle</i>, disponível também no Portal Software Público. O Eclipse e o Maven vem instalado e integrado no <i>framework</i>. O Servidor Tomcat disponível no <i>framework</i> não é recomendado, sendo melhor utilizar em separado. Também é preciso que, ao fazer a instalação e configuração, o servidor tenha acesso à internet para que o Maven possa fazer download das bibliotecas utilizadas na aplicação.</b>
	
##3 - Instalação

##3.1 - Banco de dados

<b>Passo 1:</b> Baixe o script <i>sistema_ouvidoria.sql</i> na sessão de download.

<b>Passo 2:</b> Abra o MySQL Browser, escolha a opção OpenScript do menu File e selecione o arquivo <i>sistema_ouvidoria.sql</i> para que seja aberto.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/1.png) 

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/1.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;	

<b>Passo 3:</b> Execute o script para a criação do banco de dados com os dados mínimos para configuração de um novo Órgão.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/2.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/2.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

##3.2 - Aplicação
	
<b>Passo 1:</b> Baixe os arquivos-fonte do Sistema Ouvidoria e faça a configuração do projeto no Eclipse apontando para o diretório onde serão armazenados. Para isso, abra o Eclipse, vá em “File → Import”. Abrirá a tela de seleção do tipo de importação a se fazer. Escolha a opção “Maven → Existing Maven Project”.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/3.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/3.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

Em seguida, você irá indicar ao Eclipse, onde está o código fonte da aplicação. Indique a pasta onde está o código da aplicação baixado do portal. O Eclipse irá 'enxergar' o arquivo de configuração <i>'pom.xml'</i>. Selecione o arquivo e clique em “Finish“. Após isso, o Eclipse irá verificar as dependências e fará o download automático das bibliotecas que você irá precisar.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/4.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/4.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

Obs: O arquivo <i>pom.xml</i> do Maven, assim como outros arquivos de configuração, foram configurados para funcionamento da aplicação com o servidor Tomcat. Para utilização com outros servidores de aplicações, podem ser necessárias algumas alterações no arquivo, como por exemplo, remoção de bibliotecas que o servidor já possua.

<b>Passo 2:</b> Configuração de banco nos arquivos <i>context.xml</i> e <i>hibernate.cfg.xml</i> com o nome do database, usuário e senha criados. Abra o arquivo <i>'context.xml'</i> no caminho indicado na figura abaixo.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/5.png) &nbsp;

Procure pelas linhas onde estão os parâmetros <i>“username”</i> e <i>“password”</i>. Nos valores destes parâmetros insira o nome de usuário e a senha que terão permissão de acesso ao banco de dados.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/6.png) &nbsp;

Agora, configure o arquivo <i>'hibernate.cfg.xml'</i>. O arquivo está no caminho indicado na figura abaixo.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/7.png) &nbsp;

Configure a <i>string</i> de conexão da aplicação com o banco de dados. Insira também o <i>'username</i>' e o <i>'password'</i> para acesso ao banco de dados. Não se esqueça de mudar o parâmetro “Show Sql” para <i>false</i> caso não queria que ele seja impresso no console/log.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/8.png) &nbsp;

<b>Passo 3:</b> Geração do pacote <i>“ouvidoria.war”</i> da aplicação Ouvidoria.
Antes de gerar o pacote <i>'war'</i>, é interessante que você clique com o botão direito do mouse no nome do projeto (ouvidoria) e escolha a opção “Refresh”. Também é recomendado que você clique com o botão direito do mouse no arquivo <i>'pom.xml'</i> e escolha a opção “Run as → Maven Clean”. Com isso, garantimos que o arquivo <i>'war'</i> será gerado totalmente atualizado. Feito isso, clique com o botão direito do mouse no nome do projeto (Ouvidoria), escolha a opção “Export → War File”. Escolha o local onde o arquivo será criado e clique em “Finish”.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/9.png) &nbsp;

<b>Passo 4:</b> Após gerar o arquivo <i>ouvidoria.war</i>, copie o mesmo para a pasta “webapps” do Tomcat . 

<b>Passo 5:</b> É necessário configurar alguns parâmetros da JVM que serão usados na inicialização do Tomcat.
Para um ambiente Linux, no diretório raiz do Tomcat, crie o arquivo <i>setenv.sh</i> (caso ainda não exista) e adicione a este arquivo a seguinte linha:

	export JAVA_OPTS="-server -Xms32M -Xmx256M"

Caso você tenha instalado em sua máquina, outra versão do java, é necessário também dizer ao Tomcat qual versão do Java deverá ser utilizada. Para isso, sugerimos que você procure por tutoriais adequados ao seu ambiente de trabalho, pois essa configuração varia de acordo com o sistema operacional e a versão do sistema instalado.

<b>Passo 6:</b> Após iniciar o Tomcat, acesse a aplicação pelo <i>browser</i>.  O Tomcat, por padrão, responde as requisições na porta 8080. Portanto, se as únicas modificações feitas no arquivo <i>context.xml</i> foram a do usuário e senha do banco, o caminho para acesso será [http://localhost:8080/ouvidoria](http://localhost:8080/ouvidoria).

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/10.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/10.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

##4 - Configurando um novo Órgão

<b>Passo 1:</b> Para configurar uma nova Ouvidoria, você deverá acessar a aplicação com o usuário Administrador do Sistema (CPF → 11111111111, senha → 123). Para ter acesso ao menu “Acesso Restrito” é necessário alterar a URL substituindo o trecho “MainInternet” por “MainIntranet”:

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/11.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/11.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

<b>Passo 2:</b> Após o acesso, configure os parâmetros gerais do sistema , acessando o 	menu “Administrar/Parâmetros Gerais”.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/12.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/12.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

<b>Passo 3:</b> Verifique se o campo “Diretório raiz da aplicação” foi preenchido com uma estrutura de diretório válida, com permissões de leitura e escrita para o usuário do Tomcat (novamente, para saber como fazer isso, é necessário saber qual sistema operacional e versão do sistema você está usando e buscar por um tutorial adequado, pois essas configurações podem variar). Esse será o diretório de trabalho do sistema e será usado para criar os anexos e outros arquivos necessários. Também tenha o cuidado de colocar um endereço válido para o servidor de e-mail que será usado na aplicação. Por último, tenha o cuidado de incluir uma “/” ao final do caminho do diretório raiz da aplicação.

<b>Passo 4:</b> Cadastre o um novo Órgão, acessando o menu “Administrar/Manter Órgãos”.
	
![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/13.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/13.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

Nesta parte da instalação, é preciso ter um cuidado especial com as datas de configuração do novo órgão criado. Tenha certeza que:
* A data de Inicio da Operação seja maior que a data de Fim de Cadastramento.
* A data de Inicio de Acionamento  seja maior que a data de Inicio de Cadastramento.
* A data de Inicio Consulta de Resposta seja maior que a data de Inicio de Acionamento.
* Para as datas de fim, utilize a mesma lógica usada para as Datas de Início.

<b>Passo 5:</b> Após o cadastro do novo órgão, atualize as configurações do órgão, acessando “Administrar/Manter >> Órgão”. Após isso clique no botão 	“Atualizar Configuração” pertinente ao Órgão cadastrado. Abaixo, explicações sobre os textos que são configuráveis e qual a finalidade de cada um.

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/14.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/14.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/15.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/15.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/16.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/16.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/17.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/17.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;
	
<b>Abaixo, uma explicação para os demais campos de configuração:</b>

* <b>Notificar aos responsáveis por acionamento sem resposta / Hora/Minuto do Envio de Notificação (HH:MM):</b>
O sistema pode gerar um e-mail de cobrança para os responsáveis por responder aos acionamentos abertos no sistema. Juntamente com a mensagem de cobrança, é enviado o link de acesso direto a mensagem, bem como a situação em que ela se encontra. A mensagem é enviada diariamente, no horário indicado.

* <b>Órgão permite anexar arquivo ao acionamento / Tamanho máximo para arquivos anexos (em KB):</b>
É possível permitir que sejam anexados arquivos ao acionamento. Este campo habilita esta opção, e o tamanho máximo permitido para cada anexo. O tipo de arquivo que pode ser anexado é configurado na opção “Administrar → Parâmetros Gerais”

* <b>Órgão permite mensagem digitalizada no acionamento:</b>
Funciona de maneira similar a opção anterior.

* <b>Órgão possui código de acesso:</b>
Indica se o usuário receberá um código de acesso para consulta aos acionamentos. O código de acesso é gerado junto com o protocolo de atendimento

* <b>Existe bloqueio por falhas na digitação do código de acesso /Número máximo de falhas no código de acesso /Tempo de bloqueio pelo código de acesso (em minutos):</b>
Indica se o sistema irá bloquear a consulta a um determinado protocolo, uma vez o código de acesso seja digitado errado. É necessário informar o número de tentativas erradas que irá resultar no bloqueio, e o tempo em minutos que este bloqueio irá funcionar.

* <b>Existe bloqueio por falhas na digitação da pergunta para recuperação do código de acesso / Número máximo de falhas no código de acesso / Tempo de bloqueio pelo código de acesso (em minutos):</b>
Similar a opção anterior.

* <b>Atendente pode consultar mensagens durante o atendimento:</b>
Indica se o usuário com perfil de “Atendente” poderá acessar o sistema e consultar acionamentos durante a realização de um atendimento a usuário. 
	
<b>É exigido certificado digital para acesso ao órgão e a todos os sub-órgãos / é exigido certificado digital para acesso ao órgão e opcional para todos os sub-órgãos.<b>

* <b>Nome do diretório do órgão:</b>
Aqui é informado o diretório onde serão armazenados os dados do órgão criado. Note que o nome do diretório deve ser exatamente igual ao diretório criado, pois de outro modo, os anexos e imagens não serão salvos corretamente.

<b>URL para consulta de funcionários</b>

* <b>URL de suporte ao usuário:</b>
Indica algum endereço internet/intranet que o usuário poderá acessar para ajudá-lo a fazer o acionamento de forma correta.

* <b>Remetente dos e-mails que serão enviados pela aplicação:</b>
O e-mail informado aqui será visualizado pelos usuários como o remetente de todas as mensagens do sistema. Geralmente é usado um e-mail corporativo como [ouvidoria@orgao.br](mailto:'ouvidoria@orgao.br). Não é recomendado o uso de um e-mail pessoal.

* <b>Tipos de acionador permitidos para o órgão:</b>
Indica de que maneira o usuário poderá se identificar ao fazer um acionamento.

* <b>Meios de envio de resposta permitidos para o órgão:<b/>
Indica que meio de comunicação o usuário pode informar para o recebimento de sua resposta.

<b>Passo 6:</b> Após o cadastro, altere a classe <i>OrgãoCtrl.java</i> configurando o código do órgão (variável <b>orgaoId</b>),recém cadastrado, da seguinte forma:
	
<b>a)</b> Obtenha o código do órgão recém cadastrado consultando o banco de dados da aplicação (tabela INSTITUICAO coluna COD_INSTIT).

<b>b)</b> Vá novamente ao Eclipse, encontra a classe <i>OrgãoCtrl.java</i> e substitua o código de órgão existente pelo código de órgão da nova instituição. 
	
![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/18.png) &nbsp;

Feita esta substituição, salve o arquivo e execute novamente o procedimento de criação do  pacote <i>'ouvidoria.war'</i>.

Esta parte é um pouco trabalhosa, então vamos explicar detalhadamente. Não será feito um novo “Deploy” da aplicação. Iremos apenas gerar o código fonte novamente, desta vez com o código do órgão criado. Antes de gerar o novo arquivo <i>“ouvidoria.war”</i>, pare o servidor tomcat. 

Uma vez parado o servidor, abra o arquivo <i>'ouvidoria.war'</i> com um descompactador de arquivo (os arquivos <i>'.war'</i> na verdade são arquivos compactados para serem lidos por servidores web). Depois de descompatar os arquivos, substitua os arquivos da pasta '[diretório do tomcat]/webapps/ouvidoria/', pelos novos arquivos e em seguida apague o arquivo <i>'ouvidoria.war'</i> (isto impede que o servidor enxergue o novo arquivo <i>“.war”</i> e faça um novo deploy da aplicação). Em seguida, no console do terminal, digite o comando 'touch /[diretório do tomcat]/webapps/ouvidoria/WEB-INF/web.xml”. Este comando irá modificar a data e hora do arquivo <i>web-xml</i>, e com isso o servidor tomcat irá atualizar a aplicação. Feito isso, basta reiniciar o servidor tomcat.
	
<b>Passo 7:</b> Por fim, acesse novamente a aplicação e já estará usando o novo Órgão.

<b>Para acessar a parte de “acesso restrito”, como na figura, basta editar a url de acesso no navegador, trocando a parte onde diz “MainInternet” para “MainIntranet”.</b>

![](https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/19.png)

<a href="https://raw.github.com/gabrielamayoli/Sistema-de-Ouvidoria/master/imagens/19.png" target="_blank">Clique para ver a imagem ampliada</a>
&nbsp;
	
<b>Passo 8:</b> Por fim, crie as informações necessárias para uso do sistema. A melhor ordem é se criar “Sub Órgão”, “Localidades”, “Tipos de Mensagens”, “Assuntos de 	Mensagens”, “Usuários”, nessa ordem, de forma a atender todas as dependências 	para o funcionamento do sistema. Obrigatoriamente, você precisa cadastrar um 	usuário no perfil “Ouvidor Geral”.
