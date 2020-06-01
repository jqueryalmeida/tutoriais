# Padrões para Aplicativos em PHP usando MVC
E recomendações para sua criação

## Projetos baixados da internet
Da internet em geral e do GitHub em particupar. A grande maioria dos projetos que baixo para testar não funcionam, como foi o caso dos 44 MVC que divulguei no grupo PHP BRasil, dos quais baixei 42 e testei todos. Não chegou a 5 os que consegui rodar.

Boa parte contém erros, outra parte praticamente nem tem um README ou é insuficiente para entender.
Outros não acompanham um script .sql de testes.
Ainda outros problemas.

## Publicação de projetos
As sugestões abaixo pretendem colaborar para evitar estes problemas, pois se publicamos um projeto é porque desejamos que alguém o experimente, nos dê start, nos siga, dê fork, etc.

## Este post não é lei
Mas apenas de trocar ideias. Caso não concorde pode ajudar dizendo como você usa. Apesar de poder ser polêmico, acredito que poderá ser útil para a comunidade.

Alguns são consenso na comunidade e outros são apenas a minha preferência.

Sei que a adoção de padrões pode variar de pessoa parar pessoa, mas vou divulgar os meus para ajudar quem ainda não tem o seu e tentando colaborar com quem já tem e pode otimizar.

## Sugestões
```php
Uso de .htaccess
Front controller. Somente esta pasta é acessível ao público
Constantes facilitam a comunicação entre arquivos do aplicativo
Nomes de classes: CamelCase e Nomes de métodos e de propriedades: camelCase
Gosto destes nomes: ClientesController nos nomes de classes e dos arquivos
Uso do composer com PSR-4 (facilita a criação do aplicativo) e informações sobre o aplicativo e sobre o autor
Acompanhar um detalhado README.md
Acompanhar um script sql no raiz para teste do aplicativo com facilidade
Usar código que avisa que composer ainda não foi executado (abaixo) evitando a mensagem de erro
Fornecener login e senha logo no início do README.md, caso precise de login e senha para testar aplicativo
Preferir o uso do PDO, pois é o mais usado e com mais recursos  (genérica)
Criar classes primárias em core/ e extender nas classes em app/
Ao programar ter sempre em mente de facilitar a vida do usuário (genérica)
Procurar usar as melhores práticas e as recomendações de segurança (genérica)
Nos diretórios app/ (no caso da estrutura que sugeri) inserir arquivos README.md com instruções de como o usuário proceder. Exemplo: Criar um controller, um model e uma pasta view para cada tabela extra adicionada. E sempre que achar por bem crie um README.md com orientações
Evitar comunicação direta entre view e model. Sempre intermediar essa comunicação com o controller
Usar e abusar de expressões condicionais. Exemplo abaixo (genérica)
```

## Minha estrutura preferida, 
Dividir arquivos entre app (aplicativo, negócio) e core (arquivos fixos)
```php
Raiz limpo, com apenas .htaccess, README.md e composer.json
public
  assets
app
  Controller (constrollers do aplicativo)
  Model (Models do aplicativo)
  View (Views do aplicativo)
  config.php (configurações do banco e constantes)
core (arquivos do core, não alterados pelo programador)
  bootstrap.php (início do aplicativo e algumas constantes)
  Controller.php
  ErrorController.php
  Model.php
  Router.php
```

## Alguns Códigos

### Dica legal
Que facilita a compreensão da mensagem de erro do aplicativo e mostra profissionalismo da sua parte.
São raros os aplicativos que usam algo parecido.

No arquivo que inclui o vendor/autoload.php:
```php
if(!file_exists(ROOT . 'vendor/autoload.php')){
  print '<h3 align="center" style="color:red">Antes precisa executar: composer dumpautoload no raiz do aplicativo!</h3>';
  exit;
}else{
  require_once ROOT . 'vendor/autoload.php';
}
```
```php
$params = [
    'name'          => (empty($_POST['name'])) ? '' : trim(strip_tags($_POST['name'])),
    'starting_date' => (empty($_POST['starting_date'])) ? '' : trim(strip_tags($_POST['starting_date'])),
    'ending_date'   => (empty($_POST['ending_date'])) ? '' : trim(strip_tags($_POST['ending_date'])),
    'status'        => (empty($_POST['status'])) ? 0 : trim(strip_tags($_POST['status']))
];
```
