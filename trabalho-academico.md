# Introdução

## Armazenamento de senhas

Praticamente todos os serviços que utilizamos, principalmente online, exigem autenticação por senha. Sejam nossas redes sociais, _Internet Banking_, cartões de crédito (e/ou débito), etc.

É uma recomendação básica de segurança que não se utilize a mesma senha para diversos serviços, e além disso, devemos trocar nossas senhas aproximadamente a cada 3 meses.

Seguir estas recomendações nos deixa muito mais seguros, mas também nos deixa muito mais propensos a esquecer os dados de acesso, o que provavelmente é o principal motivo para muitas pessoas não as seguirem.

Para solucionar este problema, podemos recorrer a aplicações que armazenam estas senhas (de forma segura, claro), para que não precisemos nos lembrar de todas.

Algumas aplicações que realizam este trabalho são:

- Dashlane \cite{dashlane}
- RoboForm \cite{roboform}
- LastPass \cite{lastpass}
- 1Password \cite{1password}
- Keeper \cite{keeper}

Porém, um ponto em comum destes softwares é que todos transmitem suas senhas pela internet (mesmo que encripatadas). Um usuário malicioso pode obter acesso aos seus dados e tentar decifrá-los, conseguindo assim, acesso a todas as contas cujas senhas estivessem armazenadas no _App_.

## Aplicativo _Esqueci a senha!_

Com uma proposta diferente, desenvolvi o aplicativo _Esqueci a senha!_, tendo suas vantagens e desvantagens quando comparado às soluções supracitadas.

O principal diferencial é que _Esqueci a senha!_ armazena suas senhas somente em um banco de dados no próprio celular, não transmitindo nada pela internet. Com isso, você ganha em segurança, perdendo em praticidade. As senhas só existirão em um dispositivo, e serão perdidas em caso de troca de aparelho, por exemplo.

Além disso, o aplicativo tem seu acesso protegido por uma "pergunta secreta" que o usuário deve definir em seu primeiro acesso ao mesmo. Desta forma, caso alguém ache o celular, não conseguirá acessar suas senhas, mas não será necessária **mais uma senha** para acessar o aplicativo.
