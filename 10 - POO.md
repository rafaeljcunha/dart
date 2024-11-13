### 1. Encapsulamento

Encapsulamento é o conceito de "esconder" dados ou detalhes de implementação dentro de uma classe, permitindo que os dados sejam acessados apenas através de métodos específicos (getters e setters). Isso melhora a segurança e a modularidade do código.

#### Exemplo em Dart:

```dart
class ContaBancaria {
  double _saldo; // Propriedade privada (usando o underline)

  ContaBancaria(this._saldo);

  // Getter para acessar o saldo
  double get saldo => _saldo;

  // Método para depositar dinheiro
  void depositar(double valor) {
    if (valor > 0) {
      _saldo += valor;
    }
  }

  // Método para sacar dinheiro
  void sacar(double valor) {
    if (valor > 0 && valor <= _saldo) {
      _saldo -= valor;
    } else {
      print('Saldo insuficiente');
    }
  }
}

void main() {
  var conta = ContaBancaria(1000);
  conta.depositar(500);
  conta.sacar(200);
  print('Saldo atual: ${conta.saldo}'); // Saldo atual: 1300
}
```

No exemplo acima, `_saldo` é uma variável privada, acessível apenas por métodos dentro da classe `ContaBancaria`, protegendo o dado e permitindo controle sobre como ele é manipulado.

### 2. Herança

Herança é o princípio onde uma classe pode "herdar" propriedades e métodos de outra classe, promovendo o reuso de código e facilitando a criação de hierarquias de classes.

#### Exemplo em Dart:

```dart
class Animal {
  void dormir() {
    print('O animal está dormindo.');
  }
}

class Cachorro extends Animal {
  void latir() {
    print('O cachorro está latindo.');
  }
}

class Gato extends Animal {
  void miar() {
    print('O gato está miando.');
  }
}

void main() {
  var cachorro = Cachorro();
  cachorro.dormir(); // Herda método da classe Animal
  cachorro.latir();

  var gato = Gato();
  gato.dormir(); // Herda método da classe Animal
  gato.miar();
}
```

Nesse exemplo, `Cachorro` e `Gato` são subclasses de `Animal`, herdando o método `dormir` e definindo seus próprios métodos (`latir` e `miar`).

### 3. Polimorfismo

Polimorfismo permite que classes derivadas sejam tratadas como se fossem uma instância da classe base, enquanto ainda mantêm seu comportamento específico.

#### Exemplo em Dart:

```dart
class Forma {
  void desenhar() {
    print('Desenhando uma forma genérica');
  }
}

class Circulo extends Forma {
  @override
  void desenhar() {
    print('Desenhando um círculo');
  }
}

class Quadrado extends Forma {
  @override
  void desenhar() {
    print('Desenhando um quadrado');
  }
}

void main() {
  List<Forma> formas = [Circulo(), Quadrado()];

  for (var forma in formas) {
    forma.desenhar(); // Executa o método específico de cada forma
  }
}
```

Aqui, temos uma lista de objetos `Forma`, mas cada elemento da lista é uma instância de `Circulo` ou `Quadrado`. Quando `desenhar()` é chamado, o Dart usa o método sobrescrito específico da classe real (`Circulo` ou `Quadrado`), mostrando o polimorfismo.

### 4. Abstração

A abstração envolve a criação de classes e métodos que representam conceitos genéricos, sem especificar todos os detalhes. Classes abstratas em Dart são declaradas usando a palavra-chave `abstract` e servem como um modelo para outras classes, que devem implementar os métodos abstratos.

#### Exemplo em Dart:

```dart
abstract class Veiculo {
  void ligar();

  void desligar() {
    print('Veículo desligado');
  }
}

class Carro extends Veiculo {
  @override
  void ligar() {
    print('Carro ligado');
  }
}

class Moto extends Veiculo {
  @override
  void ligar() {
    print('Moto ligada');
  }
}

void main() {
  var carro = Carro();
  carro.ligar();
  carro.desligar();

  var moto = Moto();
  moto.ligar();
  moto.desligar();
}
```

No exemplo acima, `Veiculo` é uma classe abstrata com um método abstrato `ligar()`, que deve ser implementado por classes derivadas. `Carro` e `Moto` implementam `ligar()` de maneira específica.

### 5. Composição

A composição é um princípio onde uma classe é composta de outras classes. Em vez de herdar funcionalidades, você cria classes que contêm outras classes. Isso é útil para reuso de código e é considerado uma alternativa à herança em muitos casos.

#### Exemplo em Dart:

```dart
class Motor {
  void ligar() {
    print('Motor ligado');
  }

  void desligar() {
    print('Motor desligado');
  }
}

class Carro {
  Motor motor = Motor(); // Carro tem um Motor (composição)

  void dirigir() {
    motor.ligar();
    print('Carro em movimento');
  }

  void parar() {
    print('Carro parado');
    motor.desligar();
  }
}

void main() {
  var carro = Carro();
  carro.dirigir();
  carro.parar();
}
```

Nesse exemplo, `Carro` contém um objeto `Motor`. Quando você chama `dirigir()`, o carro usa o motor, demonstrando o uso de composição.

### 6. Interfaces

Embora Dart não tenha a palavra-chave `interface`, qualquer classe pode atuar como uma interface se outra classe implementar seus métodos. Interfaces são úteis para definir contratos, onde uma classe que "implementa" uma interface é obrigada a fornecer uma implementação para todos os métodos definidos na interface.

#### Exemplo em Dart:

```dart
abstract class Pagavel {
  void realizarPagamento(double valor);
}

class CartaoCredito implements Pagavel {
  @override
  void realizarPagamento(double valor) {
    print('Pagamento de \$${valor} feito com cartão de crédito');
  }
}

class Boleto implements Pagavel {
  @override
  void realizarPagamento(double valor) {
    print('Pagamento de \$${valor} feito com boleto');
  }
}

void main() {
  List<Pagavel> pagamentos = [CartaoCredito(), Boleto()];

  for (var pagamento in pagamentos) {
    pagamento.realizarPagamento(100.0);
  }
}
```

Aqui, `Pagavel` é uma interface que define um contrato para o método `realizarPagamento()`. `CartaoCredito` e `Boleto` implementam essa interface, obrigando-se a fornecer uma implementação para o método.

### 7. Exemplo Completo: Sistema de Loja com OO

Vamos agora criar um exemplo mais completo de um sistema de loja com Dart, utilizando todos os princípios.

#### Exemplo de Sistema de Loja

```dart
abstract class Produto {
  String nome;
  double preco;

  Produto(this.nome, this.preco);

  void detalhesProduto();
}

class Eletronico extends Produto {
  String marca;

  Eletronico(String nome, double preco, this.marca) : super(nome, preco);

  @override
  void detalhesProduto() {
    print('Eletrônico: $nome, Marca: $marca, Preço: \$${preco.toStringAsFixed(2)}');
  }
}

class Livro extends Produto {
  String autor;

  Livro(String nome, double preco, this.autor) : super(nome, preco);

  @override
  void detalhesProduto() {
    print('Livro: $nome, Autor: $autor, Preço: \$${preco.toStringAsFixed(2)}');
  }
}

class Carrinho {
  List<Produto> itens = [];

  void adicionarProduto(Produto produto) {
    itens.add(produto);
    print('${produto.nome} adicionado ao carrinho.');
  }

  void exibirCarrinho() {
    print('\nItens no carrinho:');
    for (var item in itens) {
      item.detalhesProduto();
    }
  }
}

void main() {
  var celular = Eletronico('Smartphone', 1200.00, 'Samsung');
  var livro = Livro('Dart para Iniciantes', 39.90, 'Rafael Cunha');

  var carrinho = Carrinho();
  carrinho.adicionarProduto(celular);
  carrinho.adicionarProduto(livro);

  carrinho.exibirCarrinho();
}
```

Esse exemplo utiliza:

- **Abstração**: `Produto` é uma classe abstrata que serve como base para `Eletronico` e `Livro`.
- **Herança**: `Eletronico` e `Livro` herdam de `Produto`.
- **Polimorfismo**: A lista `itens` no `Carrinho` pode conter qualquer tipo de `Produto`.
- **Encapsulamento**: A classe `Carrinho` gerencia a adição de produtos e a exibição deles, escondendo como os produtos são armazenados.

Esses conceitos juntos formam a base de um sistema OO robusto.
