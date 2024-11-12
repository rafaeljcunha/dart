Em Dart, as coleções são fundamentais para armazenar e manipular dados. Dart possui diversos tipos de coleções, como listas, conjuntos (sets) e mapas. Elas podem ser **modificáveis** (permitem alterações) ou **não modificáveis** (imutáveis após a criação). Aqui estão exemplos que cobrem esses tipos e técnicas de manipulação de coleções, incluindo algumas operações avançadas.

### 1. Coleções Modificáveis

As coleções modificáveis permitem que você adicione, remova ou altere itens após a criação.

#### Lista Modificável

```dart
void main() {
  List<String> frutas = ['Maçã', 'Banana', 'Laranja'];
  frutas.add('Manga'); // Adiciona um item
  frutas.remove('Banana'); // Remove um item
  frutas[0] = 'Abacaxi'; // Modifica um item específico

  print(frutas); // [Abacaxi, Laranja, Manga]
}
```

#### Conjunto Modificável (Set)

Sets armazenam valores únicos. Em um Set modificável, é possível adicionar e remover elementos, e duplicatas são automaticamente eliminadas.

```dart
void main() {
  Set<int> numeros = {1, 2, 3};
  numeros.add(3); // Não adiciona novamente, pois 3 já existe
  numeros.add(4);
  numeros.remove(1);

  print(numeros); // {2, 3, 4}
}
```

#### Mapa Modificável (Map)

Maps armazenam pares de chave-valor, onde as chaves são únicas.

```dart
void main() {
  Map<String, int> idade = {'Alice': 30, 'Bob': 25};
  idade['Charlie'] = 35; // Adiciona um novo par chave-valor
  idade['Alice'] = 31; // Atualiza o valor de uma chave existente
  idade.remove('Bob'); // Remove o par chave-valor de Bob

  print(idade); // {Alice: 31, Charlie: 35}
}
```

### 2. Coleções Não Modificáveis (Imutáveis)

Coleções imutáveis são criadas usando `const`, garantindo que não possam ser alteradas após a criação. Isso é útil para garantir a integridade dos dados em certas partes da aplicação.

#### Lista Imutável

```dart
void main() {
  List<String> cores = const ['Vermelho', 'Verde', 'Azul'];
  // cores.add('Amarelo'); // Erro: tentativa de modificar uma coleção imutável

  print(cores); // [Vermelho, Verde, Azul]
}
```

#### Conjunto Imutável (Set)

```dart
void main() {
  Set<int> numeros = const {1, 2, 3};
  // numeros.add(4); // Erro: não é possível modificar o conjunto imutável

  print(numeros); // {1, 2, 3}
}
```

#### Mapa Imutável (Map)

```dart
void main() {
  Map<String, String> paises = const {
    'BR': 'Brasil',
    'US': 'Estados Unidos',
  };
  // paises['CA'] = 'Canadá'; // Erro: não é possível modificar o mapa imutável

  print(paises); // {BR: Brasil, US: Estados Unidos}
}
```

### 3. Coleções Avançadas e Manipulação de Dados

Dart oferece várias funções e métodos para manipulação avançada de coleções. Vamos explorar alguns exemplos úteis.

#### Mapeamento (`map`)

Aplica uma função a cada item de uma lista e retorna uma nova coleção com os resultados.

```dart
void main() {
  List<int> numeros = [1, 2, 3];
  var dobro = numeros.map((n) => n * 2).toList();

  print(dobro); // [2, 4, 6]
}
```

#### Filtragem (`where`)

Retorna uma nova coleção com os itens que satisfazem uma condição específica.

```dart
void main() {
  List<int> numeros = [1, 2, 3, 4, 5];
  var pares = numeros.where((n) => n % 2 == 0);

  print(pares); // (2, 4)
}
```

#### Redução (`reduce`)

Combina todos os elementos de uma lista em um único valor, aplicando uma função cumulativa.

```dart
void main() {
  List<int> numeros = [1, 2, 3, 4];
  int soma = numeros.reduce((a, b) => a + b);

  print(soma); // 10
}
```

#### Expansão (`expand`)

Usado para transformar cada elemento em uma coleção e, em seguida, concatená-los em uma única coleção.

```dart
void main() {
  List<List<int>> numeros = [
    [1, 2],
    [3, 4],
    [5, 6]
  ];
  var unico = numeros.expand((x) => x);

  print(unico.toList()); // [1, 2, 3, 4, 5, 6]
}
```

#### Operação `fold`

`fold` é semelhante a `reduce`, mas permite definir um valor inicial e acumular os resultados, útil para somas com valor inicial ou contagens.

```dart
void main() {
  List<int> numeros = [1, 2, 3];
  int resultado = numeros.fold(10, (a, b) => a + b); // 10 é o valor inicial

  print(resultado); // 16
}
```

#### Ordenação (`sort`)

Ordena a lista em ordem crescente ou com uma função de comparação personalizada.

```dart
void main() {
  List<String> nomes = ['Ana', 'Carlos', 'Beatriz'];
  nomes.sort();
  print(nomes); // [Ana, Beatriz, Carlos]

  nomes.sort((a, b) => b.compareTo(a)); // Ordem decrescente
  print(nomes); // [Carlos, Beatriz, Ana]
}
```

### 4. Coleções de Operações Funcionais (Coleções Avançadas)

Essas operações são úteis para manipulações complexas e fluxos de trabalho mais funcionais.

#### Agrupamento de Dados (`groupBy` com pacote `collection`)

Para agrupar dados, podemos usar o pacote `collection`, que fornece o método `groupBy`.

```dart
import 'package:collection/collection.dart';

void main() {
  var pessoas = [
    {'nome': 'Ana', 'idade': 20},
    {'nome': 'Carlos', 'idade': 20},
    {'nome': 'Beatriz', 'idade': 25},
  ];

  var agrupadoPorIdade = groupBy(pessoas, (pessoa) => pessoa['idade']);
  print(agrupadoPorIdade);
  // {20: [{nome: Ana, idade: 20}, {nome: Carlos, idade: 20}], 25: [{nome: Beatriz, idade: 25}]}
}
```

#### Coleções Imutáveis com `unmodifiable`

Para garantir que uma coleção modificável não seja alterada posteriormente, podemos usar o `UnmodifiableListView` do pacote `dart:collection`.

```dart
import 'dart:collection';

void main() {
  var listaModificavel = [1, 2, 3];
  var listaNaoModificavel = UnmodifiableListView(listaModificavel);

  // listaNaoModificavel.add(4); // Erro: coleção é imutável
  print(listaNaoModificavel); // [1, 2, 3]
}
```

#### Cópia e Modificação Segura de Coleções

Para copiar e modificar coleções, usamos métodos como `toList()` e `toSet()`, que criam novas instâncias sem alterar a coleção original.

```dart
void main() {
  var listaOriginal = [1, 2, 3];
  var copiaModificada = List.from(listaOriginal)..add(4);

  print(listaOriginal); // [1, 2, 3]
  print(copiaModificada); // [1, 2, 3, 4]
}
```

### Resumo

Esses exemplos cobrem várias técnicas de criação, modificação e manipulação de coleções no Dart. A utilização eficaz dessas operações avançadas pode melhorar a performance e legibilidade do código, facilitando o desenvolvimento de aplicações robustas e escaláveis.
