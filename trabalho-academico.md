# Introdução

Como citado no resumo, precisamos de muitas senhas para diversos serviços, que podem (e devem) ser alteradas com certa frequência.

Lembrar-se de todas é um grande desafio, e segundo aponta uma pesquisa realizada pela empresa _Intel Security_, pelo menos um terço de usuários da internet esquece uma de suas senhas pelo menos uma vez por semana \cite{pesquisa_esquecer_senhas}.

Segundo os dados desta pesquisa, a maioria dos usuários não utiliza nenhum programa especial para armazenar suas senhas, o que colabora para este alto índice de esquecimento.

Ainda segundo esta pesquisa, muitas vezes os usuários utilizam a mesma senha para acessar diversos serviços, o que vai contra recomendações e oferece risco para a segurança de suas informações.

Uma simples solução para mitigar este problema do esquecimento, possibilitando que os usuários utilizassem diversas senhas, seria o uso de programas que organizem suas senhas, permitindo uma eventual consulta.


# Soluções 

## Aplicativos existentes

Felizmente já existem aplicações que oferecem esta funcionalidade de armazenar suas senhas. Sejam estas soluções online, ou até aplicativos móveis para _smartphones_.

Algumas aplicativos que realizam este trabalho são:

- Dashlane \cite{dashlane}
- RoboForm \cite{roboform}
- LastPass \cite{lastpass}
- 1Password \cite{1password}
- Keeper \cite{keeper}

Porém, um ponto em comum destes softwares é que todos transmitem suas senhas pela internet (mesmo que encripatadas). Um usuário malicioso pode obter acesso aos seus dados e tentar decifrá-los, conseguindo assim, acesso a todas as contas cujas senhas estivessem armazenadas no _App_.

## Aplicativo _Esqueci a senha!_

Com uma proposta diferente, foi desenvolvido o aplicativo _Esqueci a senha!_, tendo algumas vantagens e desvantagens quando comparado às soluções supracitadas.

O principal diferencial é que _Esqueci a senha!_ armazena suas senhas somente em um banco de dados no próprio celular, não transmitindo nada pela internet. Com isso, você ganha em segurança, perdendo em praticidade. As senhas só existirão em um dispositivo, e serão perdidas em caso de troca de aparelho, por exemplo.

Além disso, o aplicativo tem seu acesso protegido por uma "pergunta secreta" que o usuário deve definir em seu primeiro acesso ao mesmo. Desta forma, caso alguém ache o celular, não conseguirá acessar suas senhas, mas não será necessária **mais uma senha** para acessar o aplicativo.
