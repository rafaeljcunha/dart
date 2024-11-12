Em Dart, o "casting" é usado para converter um valor de um tipo para outro tipo. Essa operação pode ser feita tanto em tipos simples (como `int` para `double`) quanto em tipos complexos, usando operadores específicos e métodos de conversão. Vejamos exemplos de como realizar conversões de tipos:

### 1. Conversão Básica de Tipos numéricos

Dart permite a conversão entre tipos numéricos, como de `int` para `double` e vice-versa, com métodos específicos.

#### Exemplo: `int` para `double` e `double` para `int`

```dart
void main() {
  int numeroInteiro = 10;
  double numeroDecimal = numeroInteiro.toDouble(); // int para double
  print(numeroDecimal); // Saída: 10.0

  double outroDecimal = 15.75;
  int outroInteiro = outroDecimal.toInt(); // double para int
  print(outroInteiro); // Saída: 15
}
```

No exemplo acima, usamos `toDouble()` para converter `int` para `double`, e `toInt()` para converter `double` para `int`. Ao converter `double` para `int`, a parte decimal é truncada.

### 2. Conversão de Strings para Tipos numéricos

Para converter uma `String` para `int` ou `double`, usamos os métodos `int.parse()` e `double.parse()`.

```dart
void main() {
  String valorInteiro = "123";
  int numeroInteiro = int.parse(valorInteiro); // String para int
  print(numeroInteiro); // Saída: 123

  String valorDecimal = "45.67";
  double numeroDecimal = double.parse(valorDecimal); // String para double
  print(numeroDecimal); // Saída: 45.67
}
```

### 3. Conversão de Tipos numéricos para String

A conversão de um número para `String` é simples, usando o método `toString()`.

```dart
void main() {
  int numeroInteiro = 123;
  String valorInteiro = numeroInteiro.toString(); // int para String
  print(valorInteiro); // Saída: "123"

  double numeroDecimal = 45.67;
  String valorDecimal = numeroDecimal.toString(); // double para String
  print(valorDecimal); // Saída: "45.67"
}
```

### 4. `as` para Casting entre Tipos Complexos

Dart permite usar o operador `as` para realizar casting em tipos de objetos dentro da hierarquia de classes, como em herança.

```dart
class Animal {
  void fazerSom() => print("Som de animal");
}

class Cachorro extends Animal {
  void latir() => print("Au Au!");
}

void main() {
  Animal animal = Cachorro();

  if (animal is Cachorro) {
    (animal as Cachorro).latir(); // Casting de Animal para Cachorro
  }
}
```

Aqui, `animal as Cachorro` realiza o casting, permitindo o uso do método `latir()` específico de `Cachorro`.

### 5. `is` e `is!` para Verificação de Tipo

Antes de fazer um casting, é uma boa prática verificar o tipo de uma variável para evitar exceções.

```dart
void main() {
  dynamic valor = 42;

  if (valor is int) {
    print("É um inteiro");
  } else if (valor is double) {
    print("É um double");
  } else {
    print("É outro tipo");
  }
}
```

Usamos `is` para verificar se `valor` é de um determinado tipo. Se `valor` não é do tipo esperado, `is!` pode ser usado para negar a verificação.

### 6. Casting de `dynamic` ou `Object` para Tipos Específicos

Em Dart, `dynamic` e `Object` podem conter qualquer tipo de dado, mas é comum querer garantir que uma variável `dynamic` tenha um tipo específico.

```dart
void main() {
  dynamic valor = "123";

  if (valor is String) {
    int numeroInteiro = int.parse(valor);
    print(numeroInteiro); // Saída: 123
  }
}
```

No exemplo acima, `valor` é verificado para o tipo `String` antes de ser convertido para `int`.

### 7. Conversão de `List<dynamic>` para `List<T>`

Ao lidar com listas que contêm elementos `dynamic`, você pode convertê-las para uma lista de um tipo específico.

```dart
void main() {
  List<dynamic> listaDinamica = [1, 2, 3, 4];

  List<int> listaInteiros = List<int>.from(listaDinamica);
  print(listaInteiros); // Saída: [1, 2, 3, 4]
}
```

Esse código converte `List<dynamic>` em `List<int>`, permitindo manipular a lista com segurança de tipos.

Esses exemplos cobrem as principais práticas de casting em Dart para diversos cenários, desde tipos primitivos até estruturas mais complexas.
