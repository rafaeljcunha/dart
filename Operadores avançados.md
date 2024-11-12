### Operadores Avançados

Dart possui operadores úteis para realizar operações avançadas de forma concisa.

- **Operador Ternário**: (`condition ? expr1 : expr2`) usado para expressões condicionais inline.
- **Operador de Coalescência Nula**: (`??`) retorna o valor da direita se o da esquerda for nulo.
- **Atribuição com Coalescência Nula**: (`??=`) atribui um valor se a variável é nula.
- **Cascade Notation**: (`..`) permite chamadas encadeadas em um objeto.

#### Exemplo com Operadores Avançados

```dart
void main() {
  // Operador ternário
  int a = 10;
  String result = (a > 5) ? 'Maior que 5' : 'Menor ou igual a 5';
  print(result); // Saída: Maior que 5

  // Operador de coalescência nula
  String? nome;
  String saudacao = nome ?? 'Olá, Visitante!';
  print(saudacao); // Saída: Olá, Visitante!

  // Atribuição com coalescência nula
  nome ??= 'João';
  print(nome); // Saída: João

  // Cascade Notation
  var pessoa = Pessoa()
    ..nome = 'Alice'
    ..idade = 25
    ..saudar();
}

class Pessoa {
  String nome = '';
  int idade = 0;

  void saudar() => print('Olá, meu nome é $nome e tenho $idade anos.');
}
```
