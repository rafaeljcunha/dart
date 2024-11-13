### Pacotes e Modularização

Para organizar um projeto Dart em módulos, é recomendável criar diferentes arquivos e pastas. O gerenciamento de pacotes é feito pelo `pubspec.yaml`.

Exemplo de estrutura de projeto:

```
lib/
├── models/
│   └── pessoa.dart
├── services/
│   └── api_service.dart
└── utils/
    └── formatter.dart
```

#### Exemplo de um Arquivo de Modelo (`pessoa.dart`)

```dart
class Pessoa {
  final String nome;
  final int idade;

  Pessoa(this.nome, this.idade);
}
```

#### Exemplo de um Serviço (`api_service.dart`)

```dart
import 'dart:convert';
import 'package:http/http.dart' as http;
import '../models/pessoa.dart';

class ApiService {
  Future<Pessoa> fetchPessoa() async {
    final response = await http.get(Uri.parse('https://api.exemplo.com/pessoa'));

    if (response.statusCode == 200) {
      return Pessoa.fromJson(jsonDecode(response.body));
    } else {
      throw Exception('Erro ao carregar dados');
    }
  }
}
```

### Exemplo de Uso dos Pacotes

O arquivo principal importa as classes dos pacotes modularizados:

```dart
import 'models/pessoa.dart';
import 'services/api_service.dart';

void main() async {
  var apiService = ApiService();
  var pessoa = await apiService.fetchPessoa();
  print('Pessoa: ${pessoa.nome}, ${pessoa.idade} anos');
}
```

Com esses exemplos, você cobre diversas funcionalidades avançadas de Dart, como operadores, testes, manipulação de arquivos, JSON, modularização e muito mais! Esses conceitos são fundamentais para construir aplicações robustas e modulares em Dart.
