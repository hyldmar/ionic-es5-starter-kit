# Ionic ES5 Starter Kit

[![Dependency Status](https://david-dm.org/loicknuchel/ionic-starter.svg)](https://david-dm.org/loicknuchel/ionic-starter)

Este projeto tem como objetivo permitir que você inicie um novo app o mais rápido possível.

Basta cloná-lo e você está pronto para começar o seu app com o básico! O código padrão já está escrito e as libs mais utilizadas estão incluídas. Tentei seguir ao máximo as melhores práticas com Angular & Ionic, estão este pode ser um bom começo para você.

Sinta-se livre para abrir uma issue para qualquer dúvida ou sugestão que você possa ter.

Esta aplicação (principalmente) segue o [Guia de Estilo sugerido por John Papa](https://github.com/johnpapa/angular-styleguide/blob/master/a1/i18n/pt-BR.md).

## Começando

- instale nodejs, npm, gulp, bower, cordova, ionic & sass (como global -g se ja nao os tiver instalado)
- `git clone git@github.com:wgbn/ionic-es5-starter-kit.git`: clone este repositorio
- `cd wgbn-ionic-starter`: entre na pasta
- `bower install`: instale as dependencias do app
- `npm install`: instale as dependencias de construçao
- `ionic setup sass`: ative o sass
- `ionic serve`: inicie o app em seu browser

Para executar o aplicativo em seu dispositivo Android:

- `ionic platform add android`: adicione a plataforma android ao seu projeto
- `ionic resources`: gere automaticamente as imagens de launcher e splash screen
- `ionic run android`: e rode o aplicativo

## Organização:

### JavaScripts

O projeto está organizado de forma que você não precisa importar seus scripts (os seus) para o index.html
Você somente precisa por no index as bibliotecas externas que você for adicionando ao projeto.

Todos os seus scripts, criados dentro da pasta `app/` serão unidos e minificados dentro do arquivo `app/js/scripts.min.js`
Para isso, antes de escrever seus arquivos rode o `$ gulp` na pasta do projeto para ficar assistindo as motificações nos seus arquivos e ir concatenando à medida que você vai desenvolvendo.

A recomendação do Style Guide do John Papa é que você separe os arquivos por área (telas), como já demonstram as duas telas do projeto base (login e main):

```
app/
  |- login
  |   |- login.ctrl.js
  |   |- login.html
  |
  |- main
  |   |- main.ctrl.js
  |   |- main.html
  |   |- main-title.directive.js
  |   |- main-title.directive.html
```

* **controllers** usam o sufixo `.ctrl.js`
* o arquivo de view leva o mesmo nome com `.html`
* **directives** que só são usadas em uma tela, devem ficar na pasta com sufixo `.directive.js`
* o template da directive deve estar no mesmo local com sufixo `.directive.html`

Para scripts que serão acessados por várias telas, como directives globais, fectorys e services, recomenda-se usar a pasta `app/common` e você pode ou não separar em subpastas dentro dela:

```
app/
  |- common
       |- directives
       |   |- h3-name.directive.js
       |   |- h3-name.directive.html
       |
       |- services
       |   |- local-storage.service.js
       |
       |- utils.service.js
```

* **services** e **factorys** usam o sufixo `.service.js`
* **directives** usam o sufixo `.directive.js`
* o template da directive deve estar no mesmo local com sufixo `.directive.html`

**Lembrando que todos estes scripts serão incluídos automaticamente em seu index.html minificados no arquivo scripts.min.js**

### SASS

Seus arquivos `.scss` devem estar na pasta `scss/` que fica fora da pasta `www/`. Para cada tela e directive que você precisa estilizar, recomenda-se colocar seus arquivos de estilo aqui.
Você pode ou não separar em pastas, como `scss/telas/` ou `scss/directives/`, o importante é que você importe-os sempre no arquivo `ionic.app.scss` como o exemplo abaixo:

```
@import "www/lib/ionic/scss/ionic";
@import '_overrides';
@import "_styles";
@import "sua-diretiva";
@import "sua-tela";
```

Se você fez sua hierarquia com pastas, seu arquivo `ionic.app.scss` ficaria parecido com este:

```
@import "www/lib/ionic/scss/ionic";
@import '_overrides';
@import "_styles";
@import "directives/sua-diretiva";
@import "telas/sua-tela";
```

Para uma organização de pastas parecida com esta:

```
|- scss
|    |- directives
|    |    |- sua-directiva.scss
|    |
|    |- telas
|    |    |- sua-tela.scss
```

## Personalização

Como é apenas um projeto modelo, você pode querer mudar o seu nome. Para isso, vocẽ terá de editar:

- `config.xml` (widget id, name, description & author)
- `www/index.html` (title)
- `bower.json` (name, homepage, author & description)
- `package.json` (name & description)
- `ionic.project` (name)

## Infos

### Specific urls

Use essas URLs personalizadas para abrir outros aplicativos usando inappbrowser (org.apache.cordova.inappbrowser)

- "tel:0123456789" => ligar para este número
- "sms:0123456789?body=coucou" => enviar sms para este número
- "geo:lat,lon" => abrir o mapa para estas coordenadas
- "mailto:toto@example.com" => enviar um e-mail

ver mais sobre http://stackoverflow.com/questions/26271313/tel-sms-and-mailto-no-longer-working-in-android-after-upgrading-to-cordo

### Outros links

- Push
    - https://github.com/hollyschinsky/PushNotificationSample
- Unit test
    - https://bradb.net/unit-testing-with-the-ionic-framework/
    - http://forum.ionicframework.com/t/ionic-and-karma-unittest/8799
- Data
    - PouchDB (http://devgirl.org/2014/12/30/sync-data-using-pouchdb-in-your-ionic-framework-app/)
