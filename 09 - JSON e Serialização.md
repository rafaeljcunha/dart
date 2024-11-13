### JSON e Serialização de Objetos

Para serializar e desserializar objetos em JSON, usamos o pacote `dart:convert`.

```dart
import 'dart:convert';

class Pessoa {
  String nome;
  int idade;

  Pessoa({required this.nome, required this.idade});

  // Convertendo um Map em um objeto Pessoa
  factory Pessoa.fromJson(Map<String, dynamic> json) {
    return Pessoa(
      nome: json['nome'],
      idade: json['idade'],
    );
  }

  // Convertendo Pessoa em um Map
  Map<String, dynamic> toJson() {
    return {
      'nome': nome,
      'idade': idade,
    };
  }
}

void main() {
  String jsonString = '{"nome": "Alice", "idade": 25}';

  // Desserializar
  Map<String, dynamic> jsonMap = json.decode(jsonString);
  var pessoa = Pessoa.fromJson(jsonMap);
  print(pessoa.nome); // Saída: Alice

  // Serializar
  String jsonEncoded = json.encode(pessoa.toJson());
  print(jsonEncoded); // Saída: {"nome":"Alice","idade":25}
}
```
