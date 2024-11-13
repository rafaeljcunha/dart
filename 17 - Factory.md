### Construtores e Fábricas

Dart oferece construtores nomeados e fábricas para criar instâncias.

```dart
class Pessoa {
  final String nome;
  final int idade;

  // Construtor nomeado
  Pessoa.anonimo() : nome = 'Anônimo', idade = 0;

  // Construtor factory
  factory Pessoa.criarComNome(String nome) {
    if (nome.isNotEmpty) {
      return Pessoa(nome: nome, idade: 30);
    }
    return Pessoa.anonimo();
  }

  Pessoa({required this.nome, required this.idade});
}

void main() {
  var pessoaAnonima = Pessoa.anonimo();
  var pessoaComNome = Pessoa.criarComNome("João");

  print(pessoaAnonima.nome); // Saída: Anônimo
  print(pessoaComNome.nome); // Saída: João
}
```
