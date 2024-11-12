Em Dart, **Streams** são fluxos de dados assíncronos que emitem uma sequência de valores ao longo do tempo. Elas são muito utilizadas para tratar eventos contínuos, como interações de usuário ou dados recebidos de uma API. Quando o assunto é Streams avançadas, destacamos dois conceitos principais: **Broadcast Streams** e **Stream Transformations**.

---

### 1. Broadcast Streams

Por padrão, uma `Stream` do tipo **single-subscription** permite apenas um único ouvinte (listener). Quando queremos múltiplos ouvintes, usamos **Broadcast Streams**. Em uma `Broadcast Stream`, vários ouvintes podem se inscrever e receber dados simultaneamente.

#### Exemplo de Broadcast Stream

```dart
import 'dart:async';

void main() {
  // Criando uma Stream Controller com broadcast
  StreamController<String> controller = StreamController<String>.broadcast();

  // Adicionando múltiplos ouvintes
  controller.stream.listen((data) => print("Ouvinte 1 recebeu: $data"));
  controller.stream.listen((data) => print("Ouvinte 2 recebeu: $data"));

  // Emitindo eventos para a Stream
  controller.sink.add("Evento 1");
  controller.sink.add("Evento 2");

  controller.close();
}
```

#### Explicação

- `StreamController.broadcast()` cria um `Stream` que suporta múltiplos ouvintes.
- Vários listeners (`ouvinte 1` e `ouvinte 2`) são adicionados ao `Stream`.
- Cada vez que um evento é emitido com `controller.sink.add`, todos os ouvintes recebem a notificação.

Broadcast Streams são ideais para casos onde vários componentes da aplicação precisam responder aos mesmos eventos.

---

### 2. Stream Transformations

**Transformações de Streams** permitem modificar, filtrar ou combinar eventos de uma Stream antes de serem enviados aos ouvintes. Em Dart, existem alguns métodos comuns para transformar Streams:

- `map`: Transforma cada item da Stream.
- `where`: Filtra eventos, permitindo apenas os que atendem a uma condição.
- `expand`: Converte cada item em uma lista e emite cada elemento individualmente.
- `take` e `skip`: Limita os eventos que serão recebidos.
- `asyncMap`: Aplica uma transformação assíncrona a cada evento.

#### Exemplo de Stream com `map` e `where`

```dart
import 'dart:async';

void main() {
  // Stream de números
  Stream<int> numeros = Stream.fromIterable([1, 2, 3, 4, 5, 6]);

  // Aplicando transformações na Stream
  numeros
      .where((numero) => numero.isEven) // Filtra apenas números pares
      .map((numero) => "Número par: $numero") // Converte para string
      .listen((data) => print(data)); // Ouve os dados transformados
}
```

#### Explicação

- `where((numero) => numero.isEven)`: Filtra os valores, permitindo apenas os números pares.
- `map((numero) => "Número par: $numero")`: Transforma cada número par em uma `String`.
- O ouvinte final recebe apenas strings com números pares.

Esse exemplo mostra como `where` e `map` podem transformar dados de uma Stream antes de serem processados.

---

### Exemplo de Transformação com `asyncMap`

O `asyncMap` é útil quando cada item da Stream precisa de uma operação assíncrona, como uma consulta a uma API ou uma leitura de arquivo.

```dart
import 'dart:async';

Future<String> obterNomeUsuario(int id) async {
  // Simulando uma chamada assíncrona
  await Future.delayed(Duration(seconds: 1));
  return "Usuário $id";
}

void main() {
  // Stream de IDs de usuários
  Stream<int> ids = Stream.fromIterable([101, 102, 103]);

  // Transformando IDs em nomes de usuário usando asyncMap
  ids
      .asyncMap((id) => obterNomeUsuario(id)) // Transformação assíncrona
      .listen((nome) => print(nome));
}
```

#### Explicação

- `asyncMap((id) => obterNomeUsuario(id))`: Converte cada ID em um nome de usuário com uma função assíncrona.
- O ouvinte final recebe o nome do usuário já processado.

---

### Exemplo de Transformação com `expand`

O método `expand` permite "explodir" cada elemento em múltiplos itens. Isso é útil quando um item da Stream representa uma lista ou conjunto de dados que você deseja emitir individualmente.

```dart
import 'dart:async';

void main() {
  Stream<List<int>> listaNumeros = Stream.fromIterable([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
  ]);

  listaNumeros
      .expand((lista) => lista) // "Explode" a lista em elementos individuais
      .listen((numero) => print(numero));
}
```

#### Explicação

- `expand((lista) => lista)`: Desmonta cada lista em elementos individuais.
- Em vez de receber listas, o ouvinte final recebe números individuais.

---

### Exemplo Completo: Broadcast Stream com Transformações

Agora, vamos combinar uma Broadcast Stream com várias transformações para criar um exemplo mais avançado. Neste exemplo, imaginamos que uma lista de pedidos de uma loja precisa ser monitorada por múltiplos ouvintes. A Stream aplica transformações para categorizar os pedidos e processar dados.

```dart
import 'dart:async';

class Pedido {
  final int id;
  final double valor;
  Pedido(this.id, this.valor);
}

void main() {
  // Criando uma Broadcast Stream de pedidos
  StreamController<Pedido> pedidosController = StreamController<Pedido>.broadcast();

  // Adicionando múltiplos ouvintes com transformações
  pedidosController.stream
      .where((pedido) => pedido.valor > 50) // Filtra pedidos com valor > 50
      .map((pedido) => "Pedido ${pedido.id} com valor alto: R\$${pedido.valor}")
      .listen((data) => print("Alerta: $data"));

  pedidosController.stream
      .map((pedido) => "Pedido #${pedido.id} recebido com valor de R\$${pedido.valor}")
      .listen((data) => print(data));

  // Emitindo pedidos
  pedidosController.sink.add(Pedido(1, 49.90));
  pedidosController.sink.add(Pedido(2, 150.0));
  pedidosController.sink.add(Pedido(3, 70.0));

  pedidosController.close();
}
```

#### Explicação

- `StreamController.broadcast()`: Permite múltiplos ouvintes.
- `where((pedido) => pedido.valor > 50)`: Filtra pedidos com valores acima de 50.
- `map((pedido) => "Pedido ${pedido.id} com valor alto: R\$${pedido.valor}")`: Converte pedidos em uma mensagem específica.
- Os ouvintes recebem mensagens filtradas e transformadas.

---

### Resumo

- **Broadcast Streams** permitem múltiplos ouvintes simultâneos e são úteis para eventos que devem ser monitorados por várias partes do código.
- **Transformações de Streams** (como `map`, `where`, `expand`, `asyncMap`) são fundamentais para manipular dados antes de eles chegarem aos ouvintes. Essas transformações tornam o tratamento de dados mais flexível e eficiente.

Esses recursos ajudam a lidar com eventos e dados assíncronos de forma mais sofisticada, melhorando a escalabilidade e a organização do código em aplicações Dart.
