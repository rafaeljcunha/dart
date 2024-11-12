Em Dart, o uso de `Future` e `Stream` é essencial para lidar com programação assíncrona, especialmente em operações como leitura/escrita de dados, solicitações HTTP e manipulação de dados em tempo real. Vamos ver alguns exemplos práticos de como usá-los.

## Future em Dart

Um `Future` representa uma operação assíncrona que retornará um valor ou um erro no futuro.

### Exemplo 1: Uso básico de Future

No exemplo abaixo, `simularOperacaoAssincrona` é uma função que retorna um `Future`, simulando uma operação que leva 2 segundos para ser concluída.

```dart
Future<String> simularOperacaoAssincrona() async {
  await Future.delayed(Duration(seconds: 2));
  return 'Operação concluída';
}

void main() async {
  print('Iniciando operação...');
  String resultado = await simularOperacaoAssincrona();
  print(resultado); // Saída: Operação concluída
}
```

### Exemplo 2: Manipulação de Erros com Future

Se ocorrer um erro durante uma operação assíncrona, podemos capturá-lo usando `try-catch`.

```dart
Future<String> operacaoComErro() async {
  await Future.delayed(Duration(seconds: 2));
  throw Exception('Erro na operação');
}

void main() async {
  print('Iniciando operação com erro...');

  try {
    String resultado = await operacaoComErro();
    print(resultado);
  } catch (e) {
    print('Erro capturado: $e'); // Saída: Erro capturado: Exception: Erro na operação
  }
}
```

### Exemplo 3: Encadeamento de Futures com then()

Podemos encadear operações futuras usando o método `then()`.

```dart
Future<String> operacao1() async {
  return 'Resultado da operação 1';
}

Future<String> operacao2(String input) async {
  return 'Resultado da operação 2 baseado em $input';
}

void main() {
  operacao1().then((resultado1) {
    return operacao2(resultado1);
  }).then((resultado2) {
    print(resultado2); // Saída: Resultado da operação 2 baseado em Resultado da operação 1
  }).catchError((erro) {
    print('Erro: $erro');
  });
}
```

## Stream em Dart

Uma `Stream` representa uma série de eventos assíncronos, permitindo a manipulação de dados conforme eles são emitidos ao longo do tempo.

### Exemplo 4: Uso básico de Stream

Aqui, criamos uma `Stream` que emite valores de 1 a 5 com um intervalo de um segundo entre cada emissão.

```dart
Stream<int> contagem() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}

void main() async {
  await for (int valor in contagem()) {
    print(valor); // Saída: 1, 2, 3, 4, 5 (com intervalo de 1 segundo entre cada)
  }
}
```

### Exemplo 5: Stream com `listen`

Podemos ouvir uma `Stream` usando o método `listen`, útil quando queremos adicionar um callback para cada evento emitido.

```dart
Stream<int> contagemComListen() async* {
  for (int i = 1; i <= 3; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}

void main() {
  contagemComListen().listen((valor) {
    print('Valor: $valor'); // Saída: Valor: 1, Valor: 2, Valor: 3 (a cada 1 segundo)
  }, onDone: () {
    print('Stream concluída');
  }, onError: (erro) {
    print('Erro: $erro');
  });
}
```

### Exemplo 6: Stream com Controle de Erros

Assim como com `Future`, podemos capturar erros em `Stream` usando o `onError`.

```dart
Stream<int> contagemComErro() async* {
  for (int i = 1; i <= 3; i++) {
    await Future.delayed(Duration(seconds: 1));
    if (i == 2) throw Exception('Erro no valor $i');
    yield i;
  }
}

void main() {
  contagemComErro().listen((valor) {
    print('Valor: $valor');
  }, onError: (erro) {
    print('Erro capturado: $erro'); // Saída: Erro capturado: Exception: Erro no valor 2
  }, onDone: () {
    print('Stream concluída');
  });
}
```

### Exemplo 7: StreamController

`StreamController` permite criar `Streams` que podem ser controladas manualmente, adicionando e fechando a stream conforme necessário.

```dart
import 'dart:async';

void main() {
  final controller = StreamController<String>();

  controller.stream.listen((valor) {
    print('Recebido: $valor');
  }, onDone: () {
    print('Stream fechada');
  });

  controller.add('Olá');
  controller.add('Mundo');

  controller.close();
}
```

### Exemplo 8: Manipulação de Streams com Transformadores

Podemos transformar uma `Stream` com métodos como `map`, `where`, etc.

```dart
Stream<int> contagemFiltrada() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}

void main() {
  contagemFiltrada()
      .where((numero) => numero % 2 == 0) // Filtra apenas números pares
      .map((numero) => 'Número par: $numero') // Transforma para uma string
      .listen((valor) {
    print(valor); // Saída: Número par: 2, Número par: 4
  });
}
```

Esses exemplos mostram o uso de `Future` e `Stream` para operações assíncronas em Dart. `Future` é útil para processos que ocorrem uma vez (por exemplo, carregar dados de uma API), enquanto `Stream` é ideal para fluxos de dados contínuos (como dados de sensores ou entradas em tempo real).
