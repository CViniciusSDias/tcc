# Introdução

Praticamente todos os serviços que utilizamos, principalmente online, exigem autenticação por senha. Sejam nossas redes sociais, Internet Banking, cartões de crédito (e/ou débito), etc.

É uma recomendação básica de segurança que não se utilize a mesma senha para diversos serviços \cite{livro_senhas}, porém lembrar-se de tantas senhas é um grande desafio, e segundo aponta uma pesquisa realizada pela empresa _Intel Security_, pelo menos um terço de usuários da internet esquece uma de suas senhas pelo menos uma vez por semana \cite{pesquisa_esquecer_senhas}.

Ainda segundo os dados desta pesquisa, a maioria dos usuários não utiliza nenhum programa especial para armazenar suas senhas, o que colabora para este alto índice de esquecimento.

A pesquisa diz também que muitas vezes os usuários utilizam a mesma senha para acessar diversos serviços, o que vai contra a recomendação supracitada e oferece risco para a segurança de suas informações.

Uma simples solução para mitigar este problema do esquecimento, possibilitando que os usuários utilizassem diversas senhas, poderia ser o uso de programas que organizem suas senhas, permitindo uma eventual consulta.

Este é o objetivo deste trabalho. Realizar o desenvolvimento de um aplicativo para armazenar de forma simples e segura todas as senhas que o usuário desejar.

Para atingir este objetivo, foi realizada uma pesquisa das soluções disponíveis no mercado, conforme pode ser conferido no Captíulo 2, o que tornou possível a coleta das informações para o levantamento do escopo descrito no Capítulo 3. A partir do momento em que o escopo foi definido, as tecnologias citadas no Capítulo 4 foram escolhidas para o desenvolvimento, que gerou a solução apresentada no Capítulo 5. No Capítulo 6 é descrita a conclusão chegada onde foi identificado o acerto das decisões tomadas devido ao sucesso alcançado com o aplicativo implementado.

# Soluções Disponíveis

## Aplicativos existentes

Após realizar uma busca por soluções existentes que pudessem auxiliar neste caso, organizando e armazenando suas senhas, foram encontradas diversas opções, tendo elas funcionalidades interessantes e com versões gratuitas, sejam elas em versões online ou até aplicativos móveis para _smartphones_.

Desta busca, foram selecionadas algumas soluções pertinentes ao contexto, sendo elas:

- Dashlane \cite{dashlane}
    - Tendo versão web e mobile, em sua versão gratuita armazena até 50 senhas. Possui versão paga que custa USD 39,96 por ano (USD 3,33 por mês), onde o usuário consegue organizar senhas de forma ilimitada, sincronizar os dados entre dispositivos, realizar backup na nuvem, etc. Tendo seu aplicativo uma interface bem simples e intuitiva, outras funcionalidades interessantes são o preenchimento automatico de formulários e dados de pagamento em algumas páginas, podendo automatizar logins e verificação da força de suas senhas armazenadas.
- RoboForm \cite{roboform}
    - Tendo 2 versões, uma individual (grátis) e uma para negócios (USD 39,95), esta aplicação está disponível para web, dispositivos desktop e smartphones. Além de armazenar suas senhas, esta aplicação oferece a opção de realizar login em determinados serviços com sua digital cadastrada no app. Sua interface é bastante semelhante dentre os dispositivos, ou seja, as versões mobile e para computadores se parecem bastante, o que traz sensação de familiaridade para quem o usa em mais de um lugar.
- LastPass \cite{lastpass}
    - Além da versão mobile, ainda existem extensões para os principais navegadores (Chrome, Firefox, Safari, Opera e Edge). Na versão gratuita, o aplicativo fornece a opção de preencher os dados de login nos serviços cadastrados, além de organizar suas senhas. Na versão paga, custando USD 2,00 por mês, é possível compartilhar senhas, logins de Wi-Fi e outros itens com quantas pessoas quiser para facilitar o acesso. Ainda há a possibilidade de criar um plano de contingência digital com acesso de emergência. Oferece ainda suporte prioritário nesta versão paga, e 1GB de armazenamento criptografado de arquivos. No plano LastPass Families, por USD 4,00 por mês tem-se 6 licenças da versão paga.
- 1Password \cite{1password}
    - Esta aplicação fornece mais opções de planos. Divididos nas categorias _Pessoal & Familiar_  e _Time e Negócios_, os planos vão de USD 2,99 até USD 7,99 por usuário por mês. As principais diferenças entre os planos são no limite de armazenamento, suporte VIP, e número de usuários. Tendo versões para Mac, iOS, Windows, Android, Linux e Chrome OS, também oferece a opção de preencher dados de login automaticamente.
- Keeper \cite{keeper}
    - Tendo seu site com um visual aparentemente mais voltado para empresas, este aplicativo está disponível nas versões pessoal, de negócio e familiar. Não há informações de versão gratuita no site, mas existe o aplicativo disponível gratuitamente para download na Play Store e App Store. Os planos exibidos no site vão de USD 2,50 por mês até USD 5,00 por mês. Além das funções citadas nas soluções anteriores, esta oferece a opção de organizar as senhas em subpastas, e gerar senhas complexas automaticamente.

## Comparativo das soluções existentes

Um comparativo das soluções existentes pode ser conferido na \autoref{tabela_apps}:

: Tabela comparativa dos aplicativos para armazenar senhas \label{tabela_apps}

|Aplicativo|Preenchimento Automático|Login com Digital|Armazenamento de Arquivos|Gerador de Senhas|
|:--------:|:----------------------:|:---------------:|:-----------------------:|:---------------:|
|Dashlane  |\textbullet             |        -        |           -             |\textbullet      |
|RoboForm  |\textbullet             |\textbullet      |           -             |        -        |
|LastPass  |\textbullet             |        -        |\textbullet              |\textbullet      |
|1Password |\textbullet             |        -        |           -             |\textbullet      |
|Keeper    |\textbullet             |        -        |\textbullet              |\textbullet      |

Porém, um ponto em comum destes softwares é que todos transmitem suas senhas pela internet (mesmo que encripatadas). Um usuário malicioso pode obter acesso aos seus dados e tentar decifrá-los, conseguindo assim, acesso a todas as contas cujas senhas estivessem armazenadas no _App_.

Após realizar esta pesquisa e comparar as soluções existentes, foi possível listar como os principais requisitos de uma futura solução, de forma simplificada:

- R01: Não transmitir senhas pela internet (armazenando-as apenas localmente)
- R02: Solicitar poucas informações do usuário
- R03: Não utilizar senha para acessar o aplicativo
- R04: Ser desenvolvido de forma que possa rodar em várias plataformas (iOS, Android e Web por meio de PWA)
- R05: Ser de código aberto
- R06: Utilizar tecnologias difundidas para ser de fácil manutenção

# Escopo do Projeto

Baseando-se nos requisitos supracitados, tornou-se possível definir um escopo para o aplicativo a ser implementado, chamado de _Esqueci a Senha!_ \cite{esqueci_a_senha}, tendo algumas vantagens e desvantagens quando comparado às soluções já existentes.

## Diferenciais

Dentre os requisitos, o principal é que _Esqueci a senha!_ armazena suas senhas somente em um banco de dados no próprio celular, não transmitindo nada pela internet. Com isso, você ganha em segurança, perdendo em praticidade. As senhas só existirão em um dispositivo, e serão perdidas em caso de troca de aparelho, por exemplo.

Para que a utilização seja simples e direta, o aplicativo armazena apenas 2 campos para cada senha:

- Onde usar;
- Senha.

Desta forma, não há necessidade de exibir vários campos que muitas vezes não seriam utilizados, sem perder a flexibilidade, sendo o campo "Onde usar" textual, em que o usuário pode escrever inclusive seu login, caso seja necessário.

Com isto, o banco de dados do projeto contém apenas 1 tabela com os campos id, onde_usar e senha. Não se faz necessária nenhuma outra tabela, pois o aplicativo (por hora) permite apenas 1 usuário por dispositivo.

Com isso, o aplicativo tem seu acesso protegido por uma "pergunta secreta" que o usuário deve definir em seu primeiro acesso ao mesmo. Desta forma, caso alguém ache o celular, não conseguirá acessar suas senhas, mas não será necessária **mais uma senha** para acessar o aplicativo. Seu funcionamento se dá da seguinte forma:

Um aplicativo que armazena senhas, deve ter algum tipo de proteção, para o caso do aparelho ir parar em mãos de terceiros.
Além disso, um usuário que faz uso deste tipo de aplicativo tende a esquecer suas senhas, logo, não seria interessante para o mesmo que o programa fosse protegido com uma outra senha, já que seria comum o esquecimento desta também.
Para isso, foi implementado o mecanismo em que o usuário no primeiro acesso à aplicação, define uma pergunta da qual apenas ele deveria saber a resposta, e a resposta desta. Assim, a cada acesso subsequente, a pergunta seria exibida, sendo necessário digitar a resposta.

## Casos de uso

As funções mais comuns do aplicativo são descritas no diagrama de casos de uso, encontrado na \autoref{casos-uso}.

![Diagrama de Casos de Uso](imagens/casos-uso.png){#casos-uso largura=80%}

Fonte: Autor.

A fim de não extender muito o texto, serão detalhados apenas os casos de uso mais pertinentes e relevantes da solução, visto que os demais são deveras simplórios, não se fazendo necessária uma descrição mais abrangente.

Em seu primeiro acesso ao aplicativo, o usuário, após ver as telas de apresentação, deve cadastrar sua pergunta secreta, resposta e e-mail para recuperação da resposta, conforme a descrição seguinte:

- **Caso de Uso**: Cadastrar pergunta secreta, resposta e e-mail de recuperação
- Pós condições: Os dados de acesso (pergunta secreta, resposta e e-mail de recuperação) serão salvos na sessão
- Cenário de sucesso:
    1. O usuário digita sua pergunta secreta
    2. O usuário digita a resposta para a pergunta
    3. O usuário digita um e-mail de recuperação, para o caso de se esquecer da resposta
    4. O usuário toca no botão "Salvar"
    5. O usuário é redirecionado para a tela de Login
- Fluxo alternativo:
    5. No caso da validação do Acesso falhar, ou seja, um dos campos estar vazio, ou o campo de e-mail não estar no formato de e-mail correto, uma mensagem de erro será exibida

Nos acessos subsequentes, após logado, o usuário pode alterar estes dados na aba de configurações, conforme a descrição seguinte:

- **Caso de Uso**: Editar pergunta secreta, resposta e e-mail de recuperação
- Pré condições: Ter os dados de acesso salvos na sessão
- Pós condições: Os dados de acesso (pergunta secreta, resposta e e-mail de recuperação) serão atualizados e salvos na sessão
- Cenário de sucesso:
    1. O usuário acessa a tela de configurações
    2. O usuário toca em "Alterar seus dados"
    3. O usuário digita sua pergunta secreta
    4. O usuário digita a resposta para a pergunta
    5. O usuário digita um e-mail de recuperação, para o caso de se esquecer da resposta
    6. O usuário toca no botão "Salvar"
    7. Uma mensagem de sucesso ("Dados alterados com sucesso") é exibida
    8. O usuário é redirecionado de volta à tela de configurações
- Fluxo alternativo:
    7. No caso da validação do Acesso falhar, ou seja, um dos campos estar vazio, ou o campo de e-mail não estar no formato de e-mail correto, uma mensagem de erro será exibida

Para fazer login, o usuário precisa digitar a resposta para sua pergunta secreta que estará sendo exibida.

- **Caso de Uso**: Login
- Pré condições: Ter os dados de acesso salvos na sessão
- Pós condições: Ser redirecionado para a página de listagem de senhas
- Cenário de sucesso:
    1. Tela de login é exibida, mostrando a pergunta secreta
    2. O usuário digita a resposta correta para a pergunta
    3. O usuário é redirecionado para a página de listagem de senhas
- Fluxo alternativo:
    2. O usuário digita a resposta incorreta para a pergunta
    3. Uma mensagem de erro ("Dados inválidos") é exibida na tela

## Aplicação híbrida

Pensando na portabilidade entre plataformas, ou seja, na possibilidade de executar o aplicativo tanto em sistemas Android quanto iOS, o aplicativo foi desenvolvido de forma híbrida, combinando características do desenvolvimento Web e Nativo.

Este modelo ainda é bastante utilizado e foi um grande impulsionador do que hoje conhecemos como PWA \cite{livro_pwa}.

Ele funciona da seguinte forma: Toda a aplicação é desenvolvida utilizando as tecnologias Web, ou seja, HTML, CSS e JS. Desta forma, toda a interface e principais funcionalidades do aplicativo são criadas. Faz-se uso de alguma ferramenta que envolva esta aplicação Web, de forma que gere um arquivo instalável em dispositivos móveis, o qual poderá ser enviado para as lojas (Play Store da Google e App Store da Apple).

Este tipo de ferramenta cria um aplicativo nativo, contendo um componente chamado de _WebView_, que tem como propósito exibir páginas da Web. Este componente é carregado com nossa aplicação Web sendo executada em tela cheia, o que dá a sensação de ser nativo. Além disso, algumas ferramentas ainda fornecem _plugins_ para algumas funcionalidades nativas, como acesso a contatos, arquivos, etc.

# Tecnologias utilizadas

## Cordova

A ferramenta utilizada para desenvolver a solução de forma híbrida foi o _Apache Cordova_ \cite{livro_cordova}, que é a mais conhecida e difundida no meio.

Desenvolvido por uma empresa chamada _Nitobi_ e comparada pela _Adobe Systems_ em 2011, o projeto se chamava _PhoneGap_. Logo após a compra, uma versão de código aberto do software foi lançada, recebendo o nome _Apache Cordova_ devido à sua licença (Apache License \cite{apache_license}).

Os plugins utilizados foram os seguintes:

- cordova-plugin-device: Plugin que fornece acesso a um objeto global `device`, que permite acesso a informações do dispositivo, como modelo, plataforma, versão, etc;
- cordova-plugin-firebase-analytics: Plugin que permite o envio de informações para o _Firebase Analytics_, que monitora o acesso a cada tela;
- cordova-plugin-splashscreen: Plugin que permite a exibição de uma _SplashScreen_ (tela com a logo do projeto) antes da execução do aplicativo;
- cordova-plugin-whitelist: Plugin que, dentre outras coisas, libera acesso do aplicativo à internet;
- ionic-plugin-keyboard: Plugin que faz com que a aplicação web se comporte como nativa, não se alterando com a abertura do teclado em campos de digitação.

## Ionic

O _Apache Cordova_ não fornece nenhum tipo de interface personalizada para que desenvolvamos nossa aplicação de forma semelhante às aplicações nativas. Todo este trabalho deveria ser feito através de códigos CSS.

Para facilitar esta tarefa, existe um projeto chamado _Ionic Framework_ \cite{livro_ionic}, que fornece componentes prontos que se adaptam à plataforma utilizada, ou seja, o visual do aplicativo no Android e no iOS fica ligeiramente diferente, se parecendo com um aplicativo nativo de cada plataforma, mesmo tendo sido escrito apenas uma base de código.

Este projeto faz uso de um framework JavaScript chamado _Angular_.

## Angular

O framework Angular \cite{livro_angular} foi criado pela Google, e tem como principal característica a possibilidade de criação de componentes, que podem ser estilizados de forma independente, e utilizados dentro de outros componentes.

Utilizando Angular, o Ionic consegue criar componentes estilizados, e fazendo uso do plugin `cordova-plugin-device`, consegue formatar os mesmos de acordo com a plataforma utilizada, ou seja, oferecer aparências diferentes para Android e iOS, por exemplo.

## Web SQL Database

Devido à simplicidade dos dados armazenados, não foi necessária uma grande análise sobre a melhor forma de armazená-los, logo, um simples banco de dados relacional foi utilizado devido à maior familiaridade com este tipo de tecnologia.

O banco de dados relacional utilizado na Web é chamado de _Web SQL Database_ \cite{livro_storage}, e fornece funcionalidades simples como criação e manipulação de tabelas, o que foi suficiente para o projeto.

# Especificação da Solução Desenvolvida: _Esqueci a Senha!_

## Arquitetura do projeto

### Padrão arquitetural

O projeto foi organizado estruturalmente, de forma com que uma classe é responsável por exibir a tela, enquanto outra é responsável por realizar ações e fornecer serviços, sendo outra responsável por representar os dados da aplicação. Para seguir esta linha, foi utilizado um padrão arquitetural chamado de MVC \cite{deisgn_patterns}.

Este padrão, da forma como é utilizado hoje, consisiste em dividir o sistema em 3 camadas. Uma camada representa o dado a ser exibido e/ou manipulado, que é chamada de _Model_. Uma outra camada cuida da visualização deste dado, chamada de _View_. A terceira camada, chamada de _Controller_ faz a interação entre as duas anteriores.

No caso do aplicativo, o componente que monta a tela, é o Controller. O arquivo de template, em html, é a View, e a classe que representa o dado, como a senha, por exemplo, é nosso Model.

Diversos frameworks e ferramentas Web adotam este padrão, o que faz com que ele seja amplamente conhecido, fazendo com que uma eventual manutenção de outro programador familiarizado com o ambiente Web seja facilitada.

### Diretórios de arquivos

- app/
    - Pasta que contém o componente inicial da aplicação, que decide se a tela de login ou tela de cadastro da pergunta secreta será exibida
- assets/
    - Pasta de imagens, onde estão contidos os ícones da aplicação
- components/
    - Pasta que contém componentes compartilhados entre telas, como o cabeçalho, botões, etc.
- daos/
    - Pasta que contém os arquivos que fazem aceso aos dados, no caso, ao Web SQL Database
- models/
    - Pasta que contém a definição das classes de negócio
- pages/
    - Pasta que contém a definição das telas do aplicativo
- providers/
    - Pasta que contém definição de classes utilizadas nas páginas, que fornecem algum tipo de serviço, como criar conexão com o banco, criar alertas para a tela, etc.
- theme/
    - Pasta que contém o arquivo com o esquema de cores do aplicativo
- declarations.d.ts
    - Arquivo que contém a definição de tipos desconhecidos pelo TypeScript
- index.html
    - Arquivo principal do aplicativo, que exibe o componente inicial
- manifest.json
    - Arquivo contendo dados da aplicação para que possa ser utilizado como PWA
- service-worker.js
    - Arquivo que realiaria tarefas em segundo plano, caso necessário

## Diagrama de classes

As principais classes de negócio, e classes fornecedoras de serviços que usam, ou são usadas nas classes de negócios estão descritas no diagrama de classes, que pode ser conferido na \autoref{diagrama-classes}.

![Diagrama de Classes](imagens/diagrama-classes.png){#diagrama-classes largura=100%}

Fonte: Autor.

A classe _Senha_ representa uma senha armazenada pelo usário, e na tela inicial, é exibido uma lista de objetos deste tipo. Já a classe _Acesso_ representa os dados necessários para acessar o aplicativo, que são a pergunta secreta e sua resposta. No objeto desta classe é armazenado também o e-mail do usuário, para o caso dele esquecer a resposta, e precisar recuperá-la.

Estas classes têm métodos para validar seus dados, e nestes métodos a classe _StringHelper_ é utilizada, podendo verificar se uma string está vazia, ou está no formato de e-mail.

Para buscar os dados de acesso (pergunta secreta e sua resposta), o serviço _AcessoService_ é utilizado, buscando as informações da sessão. Este serviço também informa se é ou não o primeiro acesso do usuário ao aplicativo.

A classe _Login_ é a classe responsável por utilizar _AcessoService_ para recuperar os dados da sessão e verificar se batem com os dados digitados pelo usuário.

A classe _SenhaDao_ é a que acessa o banco de dados e realiza as operações de criar, recuperar, atualizar e remover senhas. Ela precisa de uma conexão com o banco de dados, que é criada pela classe _ConnectionFactory_.

## Exemplos de código

### Tela de exibição de senhas

Para exemplificar como é o código de uma tela, pode ser conferido o exemplo do componente TS, ou seja, o _Controller_. Nele, temos alguns métodos do ciclo de vida do componente, como `ionViewWillEnter`, executado antes da tela ser carregada, e `ionViewDidEnter`, executado após entrar na tela. Nestes métodos podem ser executadas algumas ações, como buscar os dados a serem exibidos, realizar logs, enviar dados estatísticos, etc.

```
// ...
@Component({
    selector: 'page-home',
    templateUrl: 'home.html'
})
export class HomePage {
    public senhas: Senha[] = [];
    public inicializado: boolean = false;

    // ...

    public ionViewWillEnter(): void {
        this.buscarSenhas();
    }

    public ionViewDidEnter() {
        this.firebase.logPageView('home');
    }

    private buscarSenhas(): void {
        let loading = this.loadingCtrl.create({
            content: 'Carregando'
        });

        loading.present().then(() => {
            this.senhaDao.buscarTodas()
                .then(senhas => {
                    this.senhas = senhas;
                    loading.dismiss();
                    this.inicializado = true;
                });
        });
    }

    public remover(senha: Senha): void {
        this.alertFactory.getConfirm(
            'Apagar',
            `Tem certeza que deseja apagar a senha de ${senha.ondeUsar}?`
        ).then(() => {
            this.senhas.splice(this.senhas.indexOf(senha), 1);
            this.senhaDao.remover(senha);
            this.toast.showToastWithButton('Senha removida com sucesso', 'Ok');
        }).catch(() => {/*Usuário clicou em 'não'*/});
    }

    public actionSheet(senha: Senha): void {
        this.actionSheetCtrl.create({
            title: senha.ondeUsar,
            buttons: [
                {
                    text: 'Excluir',
                    role: 'destructive',
                    icon: 'trash',
                    handler: () => { this.remover(senha); }
                },
                {
                    text: 'Editar',
                    icon: 'create',
                    handler: () => { this.navCtrl.push(EditarPage, {senha: senha}); }
                },
                {
                    text: 'Cancelar',
                    role: 'cancel',
                    icon: 'close'
                }
            ]
        }).present();
    }
}
```

A primeira linha exemplificada contém o que é chamado de _Decorator_ do TypeScript, que identifica que esta classe representa um componente do Angular. Neste _Decorator_, podemos passar informações como qual o seletor, ou seja, o nome da tag deste componente, e qual o caminho do seu template.

No método `buscarSenhas()`, faz-se uso de um componente do Ionic chamado LoadingController \cite{loading_controller}, que exibe um ícone de "carregando". Após buscar as senhas no banco de dados, este ícone é escondido pelo código `loading.dismiss()`.

Já no método `remover(senha: Senha)`, é utilizado o AlertController \cite{alert_controller} que exibe uma mensagem perguntando ao usuário se ele realmente deseja excluir a senha na qual ele clicou. Caso o usuário selecione a opção "Sim", a senha é removida do array que é exibido na tela, excluído do banco, e uma pequena mensagem de sucesso é exibida. Caso o usuário selecione a opção "Não", a pergunta é escondida, e nenhuma ação é realizada.

Já para exemplificar o template, ou seja, a _View_ de uma tela, podemos ver o código em HTML. Nele, podemos acessar todos as propriedades e métodos públicos do _Controller_, e assim, recuperar dados para exibí-los, e executar ações sobre eles. Desta forma que a classe _Controller_ `HomePage` faz a ligação entre a camada de _View_ (template) e a camada _Model_ (senhas).

```
<ion-header>
    <page-header>
        Home
    </page-header>
</ion-header>

<ion-content padding>
    <ion-list *ngIf="senhas.length">
        <ion-item *ngFor="let senha of senhas" (click)="actionSheet(senha)">
            <ion-item class="senha">
                <ion-icon name="lock" item-start></ion-icon>
                <h2>{{senha.ondeUsar}}</h2>
                <p>{{senha.senha}}</p>
            </ion-item>
        </ion-item>
    </ion-list>

    <ion-grid *ngIf="!senhas.length && inicializado">
        <ion-row align-items-center>
            <ion-col>
                <p><b>Você ainda não tem nenhuma senha cadastrada</b></p>
                <p>Navegue até a aba "Adicionar" abaixo para criar uma</p>
            </ion-col>
        </ion-row>
    </ion-grid>
</ion-content>
```

Ao clicar em uma senha, o método `actionSheet` é chamado, utilizando o ActionSheetController \cite{action_sheet} que exibe as ações existentes, ou seja, editar e remover a senha.

### Criação do banco de dados

A classe que gera a conexão com o banco de dados também realiza a criação do esquema no banco. Desta forma, na primeira conexão com o banco, a tabela será criada, conforme pode ser observado no construtor da classe `ConnectionFactory`, que executa o método `createSchema`, rodando o código SQL.

No código SQL é utilizado o comando `CREATE TABLE IF NOT EXISTS`, que antes de criar a relação verifica se a mesma já existe. Logo, não haverá a possibilidade de acontecer um erro ao tentar criar uma tabela já existente.

```
export class ConnectionFactory {

    public getConnection() {
        let db = openDatabase('senhas', '1.0', 'senhas', 2 * 1024 * 1024);

        this.createSchema(db);
        return db;
    }

    private createSchema(db) {
        let sql = `
            CREATE TABLE IF NOT EXISTS senha (
                id INTEGER PRIMARY KEY,
                onde_usar TEXT NOT NULL,
                senha TEXT NOT NULL
            );
        `;

        db.transaction(tx => tx.executeSql(sql, []));
    }
}
```

# Resultaado obtido

Com todo o estudo previamente citado, escopo e requisitos definidos e as escolhas de tecnologias, a implementação se deu de forma rápida e simples, gerando o aplicativo exibido nas telas a seguir.

## Telas

Ao abrir o aplicativo, o usuáraio se depara com uma _SplashScreen_ contendo a logo do aplicativo. A tela pode ser conferida na \autoref{tela-splash}.

![Splash Screen](imagens/prints/01-splash.jpg){#tela-splash largura=100%}

Fonte: Aplicativo _Esqueci a Senha!_.

Após ler os slides de apresentação exibidos na tela seguinte, o usuário encontra a tela para cadastrar sua pergunta secreta, resposta e e-mail de recuperação, conforme a \autoref{tela-pergunta}

![Cadastro dos Dados de Acesso](imagens/prints/06-pergunta-secreta.jpg)(#tela-pergunta largura=100%)

Fonte: Aplicativo _Esqueci a Senha!_.

Digitando os dados e clicando em "Salvar", o usuário é conduzido para a página de login. Ver \autoref(tela-login).

![Login](imagens/prints/08-login.jpg){#tela-login largura=100%}

Fonte: Aplicativo _Esqueci a Senha!_.

Após se logar, o usuário vê a tela de exibição de senhas, porém sem nenhuma cadastrada ainda, conforme \autoref{tela-sem-senhas). Então ele pode clicar na aba "Adicionar", e inserir os dados de uma nova senha na tela exemplificada na \autoref{tela-nova-senha}. Clicando em "Salvar", uma mensagem de sucesso é exibida. O usuáiro pode agora clicar em "Home", para visualizar a lista de senhas, que agora contém 1 cadastrada, conforme \autoref{tela-senhas}.

![Home sem senhas](imagens/prints/09-home.jpg){#tela-sem-senhas largura=100%}

Fonte: Aplicativo _Esqueci a Senha!_.

![Adicionar nova senha](imagens/prints/11-adicionar.jpg){#tela-nova-senha largura=100%}

Fonte: Aplicativo _Esqueci a Senha!_.

![Home com uma senha](imagens/prints/13-home.jpg){#tela-senhas largura=100%}

Fonte: Aplicativo _Esqueci a Senha!_.

Para editar ou remover uma senha, basta que o usuário toque em uma das senhas, e as opções serão exibidas para ele, conforme \autoref{tela-action-sheet}

![Ações com a senha](imagens/prints/14-action-sheet.jpg){#tela-action-sheet largura=100%}

Fonte: Aplicativo _Esqueci a Senha!_.

# Conclusão

Analisando os resultados obtidos levando em consideração o nível de experiência existente antes do início do projeto, constata-se que mesmo com um escopo limitado e funções básicas, o aplicativo _Esqueci a Senha!_ se mostrou um ótimo exemplo de como a produtividade pode ser aumentada fazendo uso de tecnologias híbridas de desenvolvimento mobile, não tendo sido necessário nenhum conhecimento de arquitetura nativa de algum sistema operacional ou dispositivo.

A plataforma de acesso ao dispositivo fonecido pelo Apache Cordova e os componentes visuais e estruturais oferecidos do Ionic Framework foram mais do que suficientes para o desenvolvimento do projeto em questão, sendo possível extender o programa com novas funcionalidades sem maiores dificuldades, caso seja necessário.

Os estudos feitos ao longo do desenvolvimento deste trabalho também mostraram que a possibilidade de desenvolver um aplicativo utilizando apenas tecnologias Web, ou seja, PWAs é enorme, e que é esperado que mais soluções e técnicas para este tipo de implementação apareçam com o passar do tempo, evoluindo cada vez mais.
