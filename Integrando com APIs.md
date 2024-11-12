Para realizar interações com APIs em Dart, você pode usar o pacote `http`, que oferece métodos convenientes para realizar requisições HTTP. Vou explicar cada tipo de requisição, como configurá-la, e como manipular as respostas e erros.

Primeiro, você precisa adicionar o pacote `http` ao seu projeto. No arquivo `pubspec.yaml`, adicione a dependência:

```yaml
dependencies:
  http: ^0.13.4
```

Depois, importe o pacote no seu código Dart:

```dart
import 'package:http/http.dart' as http;
import 'dart:convert'; // Para trabalhar com JSON
```

### 1. Requisição `GET`

O método `GET` é utilizado para buscar informações de uma API. Esse método não envia dados no corpo da requisição, apenas nos parâmetros da URL.

#### Exemplo de Requisição `GET`

```dart
Future<void> buscarDados() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/posts');

  try {
    final resposta = await http.get(url);

    if (resposta.statusCode == 200) {
      List dados = jsonDecode(resposta.body);
      print('Dados recebidos: $dados');
    } else {
      print('Erro ao buscar dados: ${resposta.statusCode}');
    }
  } catch (e) {
    print('Erro: $e');
  }
}

void main() {
  buscarDados();
}
```

### Explicação

- **`Uri.parse`**: Converte a URL em um objeto `Uri`, facilitando o manuseio de parâmetros de consulta e a construção da URL.
- **`http.get(url)`**: Realiza a requisição `GET`.
- **`jsonDecode`**: Converte o corpo da resposta (em JSON) para uma lista ou mapa que pode ser manipulado no Dart.
- **Verificação `statusCode`**: Verifica se o status da resposta é 200 (OK) antes de processar os dados.

### 2. Requisição `POST`

O método `POST` é usado para enviar dados para a API, como ao criar um novo recurso. Diferente do `GET`, `POST` geralmente inclui dados no corpo da requisição.

#### Exemplo de Requisição `POST`

```dart
Future<void> enviarDados() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/posts');
  final headers = {'Content-Type': 'application/json'};
  final corpo = jsonEncode({
    'title': 'Novo Post',
    'body': 'Este é o conteúdo do post.',
    'userId': 1,
  });

  try {
    final resposta = await http.post(url, headers: headers, body: corpo);

    if (resposta.statusCode == 201) {
      print('Dados enviados com sucesso: ${resposta.body}');
    } else {
      print('Erro ao enviar dados: ${resposta.statusCode}');
    }
  } catch (e) {
    print('Erro: $e');
  }
}

void main() {
  enviarDados();
}
```

### Explicação

- **`headers`**: Define o tipo de conteúdo como `application/json` para indicar que o corpo da requisição está em JSON.
- **`jsonEncode`**: Converte o mapa em uma string JSON para enviar no corpo da requisição.
- **`http.post`**: Realiza a requisição `POST`.
- **Status Code 201**: Indica que um recurso foi criado com sucesso (sucesso típico para `POST`).

### 3. Requisição `PUT`

O método `PUT` é usado para atualizar recursos existentes na API, enviando dados no corpo da requisição, assim como no `POST`.

#### Exemplo de Requisição `PUT`

```dart
Future<void> atualizarDados() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/posts/1');
  final headers = {'Content-Type': 'application/json'};
  final corpo = jsonEncode({
    'title': 'Post Atualizado',
    'body': 'Conteúdo atualizado do post.',
    'userId': 1,
  });

  try {
    final resposta = await http.put(url, headers: headers, body: corpo);

    if (resposta.statusCode == 200) {
      print('Dados atualizados com sucesso: ${resposta.body}');
    } else {
      print('Erro ao atualizar dados: ${resposta.statusCode}');
    }
  } catch (e) {
    print('Erro: $e');
  }
}

void main() {
  atualizarDados();
}
```

### Explicação

- **`http.put`**: Realiza a requisição `PUT`.
- **Status Code 200**: Indica que o recurso foi atualizado com sucesso.

### 4. Requisição `DELETE`

O método `DELETE` é usado para excluir um recurso específico da API.

#### Exemplo de Requisição `DELETE`

```dart
Future<void> deletarDados() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/posts/1');

  try {
    final resposta = await http.delete(url);

    if (resposta.statusCode == 200) {
      print('Recurso deletado com sucesso');
    } else {
      print('Erro ao deletar recurso: ${resposta.statusCode}');
    }
  } catch (e) {
    print('Erro: $e');
  }
}

void main() {
  deletarDados();
}
```

### Explicação

- **`http.delete`**: Realiza a requisição `DELETE`.
- **Status Code 200**: Indica que a exclusão foi realizada com sucesso.

### 5. Tratamento de Erros

Sempre que se lida com APIs, é importante incluir o tratamento de erros para lidar com falhas de conexão, respostas inválidas ou outros problemas.

#### Exemplo de Tratamento de Erros com `try-catch`

Usamos `try-catch` em todos os exemplos acima para capturar qualquer erro que possa ocorrer durante a requisição. Se ocorrer uma exceção, ele imprime o erro.

### 6. Timeout de Requisição

Para evitar que uma requisição demore muito, você pode definir um tempo limite (`timeout`).

```dart
Future<void> buscarComTimeout() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/posts');

  try {
    final resposta = await http.get(url).timeout(Duration(seconds: 5));

    if (resposta.statusCode == 200) {
      print('Dados recebidos: ${jsonDecode(resposta.body)}');
    } else {
      print('Erro: ${resposta.statusCode}');
    }
  } catch (e) {
    print('Erro: $e');
  }
}

void main() {
  buscarComTimeout();
}
```

### Explicação

- **`timeout(Duration(seconds: 5))`**: Define um limite de tempo para a requisição (neste caso, 5 segundos). Se o tempo for excedido, um erro será lançado, e a operação será interrompida.

### Resumo

Aqui está uma visão geral dos métodos:

- **GET**: Recupera dados de uma API.
- **POST**: Envia novos dados para a API.
- **PUT**: Atualiza dados existentes.
- **DELETE**: Remove um recurso da API.
- **timeout**: Define um tempo máximo para aguardar a resposta da API.
- **try-catch**: Captura e manipula erros durante as requisições.

Esses métodos e técnicas fornecem uma base sólida para trabalhar com APIs em Dart.
