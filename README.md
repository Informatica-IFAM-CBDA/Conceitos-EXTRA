# Programação Orientada a Objetos (POO) com PHP

Conceitos: Tratamento de Exceções, Interface Gráfica com Orientação a Objetos, Componentes Visuais, Desenvolvimento de Aplicações com Conexão a Banco de Dados

## Tratamento de Exceções

Definição: Tratamento de exceções é uma técnica utilizada para lidar com erros e situações inesperadas durante a execução de um programa. Em PHP, utilizamos as palavras-chave try, catch e finally.

### Exemplo em PHP:

```php
<?php
function dividir($numerador, $denominador) {
    if ($denominador == 0) {
        throw new Exception("Divisão por zero.");
    }
    return $numerador / $denominador;
}

try {
    echo dividir(10, 0);
} catch (Exception $e) {
    echo "Erro: " . $e->getMessage();
} finally {
    echo " Finalizando execução.";
}
?>
```

## Interface Gráfica com Orientação a Objetos

Definição: Interface gráfica (GUI) com orientação a objetos envolve a criação de interfaces de usuário utilizando classes e objetos. Em PHP, podemos utilizar frameworks como Laravel e Symfony para criar GUIs.

### Exemplo com Laravel:

```php
// Rota no Laravel
Route::get('/form', [FormController::class, 'showForm']);

// Controlador
class FormController extends Controller {
    public function showForm() {
        return view('form');
    }
}
```
```html
// View (form.blade.php)
<!DOCTYPE html>
<html>
<head>
    <title>Formulário</title>
</head>
<body>
    <form action="/submit" method="POST">
        @csrf
        <label for="name">Nome:</label>
        <input type="text" id="name" name="name">
        <button type="submit">Enviar</button>
    </form>
</body>
</html>
```

## Componentes Visuais

Definição: Componentes visuais são elementos da interface gráfica que permitem a interação do usuário com a aplicação, como botões, caixas de texto, tabelas, etc.

### Exemplo com Bootstrap:

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css">
</head>
<body>
    <div class="container">
        <h1>Formulário</h1>
        <form>
            <div class="form-group">
                <label for="name">Nome:</label>
                <input type="text" class="form-control" id="name" name="name">
            </div>
            <button type="submit" class="btn btn-primary">Enviar</button>
        </form>
    </div>
</body>
</html>
```

## Desenvolvimento de Aplicações com Conexão a Banco de Dados

Definição: Envolve a criação de aplicações que interagem com bancos de dados para armazenar, recuperar e manipular dados. Em PHP, podemos utilizar PDO (PHP Data Objects) para conectar a diferentes bancos de dados.

### Exemplo em PHP com PDO:

```php
<?php
$dsn = 'mysql:host=localhost;dbname=meu_banco';
$username = 'root';
$password = '';

try {
    $pdo = new PDO($dsn, $username, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $stmt = $pdo->prepare("SELECT * FROM usuarios");
    $stmt->execute();

    $result = $stmt->fetchAll(PDO::FETCH_ASSOC);
    foreach ($result as $row) {
        echo $row['nome'] . "<br>";
    }
} catch (PDOException $e) {
    echo "Erro: " . $e->getMessage();
}
?>
```

# Atividades Práticas

### 1. **Tratamento de Exceções**: Crie uma função que realiza operações matemáticas e implemente tratamento de exceções para divisões por zero.

### 2. **Interface Gráfica**: Utilize Laravel para criar um formulário simples que coleta dados do usuário.

### 3. **Componentes Visuais**: Adicione componentes visuais ao formulário utilizando Bootstrap.

### 4. **Conexão a Banco de Dados**: Desenvolva uma aplicação que conecta a um banco de dados MySQL, insere e exibe dados de uma tabela.
