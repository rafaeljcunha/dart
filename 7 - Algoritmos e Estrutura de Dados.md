Aqui estão exemplos de **algoritmos** e **estruturas de dados** implementados em Dart, cobrindo uma variedade de operações comuns, como pesquisa, ordenação e manipulação de listas.

## 1. Estruturas de Dados em Dart

### Lista (List)

A lista é uma estrutura de dados que armazena elementos de forma ordenada.

#### Exemplo: Criando uma Lista e Manipulando Elementos

```dart
void main() {
  List<int> numeros = [10, 20, 30, 40];
  numeros.add(50); // Adiciona um elemento
  numeros.remove(20); // Remove o elemento com valor 20
  print(numeros); // Saída: [10, 30, 40, 50]

  // Acessando elementos
  print(numeros[0]); // Saída: 10
}
```

### Conjunto (Set)

O `Set` armazena elementos únicos e não garante a ordem dos itens.

```dart
void main() {
  Set<int> numerosUnicos = {1, 2, 3, 3, 4}; // Valores duplicados são ignorados
  numerosUnicos.add(5);
  numerosUnicos.remove(1);

  print(numerosUnicos); // Saída: {2, 3, 4, 5}
}
```

### Mapa (Map)

Um `Map` armazena pares chave-valor, útil para associar dados.

```dart
void main() {
  Map<String, int> idades = {'Alice': 25, 'Bob': 30};

  idades['Charlie'] = 35; // Adiciona um novo par
  idades.remove('Alice'); // Remove o par com chave 'Alice'

  print(idades); // Saída: {Bob: 30, Charlie: 35}
  print(idades['Bob']); // Saída: 30
}
```

## 2. Algoritmos Comuns em Dart

### Pesquisa Linear

A pesquisa linear percorre uma lista para encontrar um elemento específico.

```dart
int pesquisaLinear(List<int> lista, int valor) {
  for (int i = 0; i < lista.length; i++) {
    if (lista[i] == valor) {
      return i; // Retorna o índice do valor encontrado
    }
  }
  return -1; // Retorna -1 se o valor não for encontrado
}

void main() {
  List<int> lista = [10, 20, 30, 40, 50];
  int posicao = pesquisaLinear(lista, 30);
  print(posicao); // Saída: 2 (índice do elemento 30)
}
```

### Pesquisa Binária

A pesquisa binária é mais eficiente que a pesquisa linear, mas exige que a lista esteja ordenada.

```dart
int pesquisaBinaria(List<int> lista, int valor) {
  int inicio = 0;
  int fim = lista.length - 1;

  while (inicio <= fim) {
    int meio = (inicio + fim) ~/ 2;
    if (lista[meio] == valor) {
      return meio; // Retorna o índice do valor encontrado
    } else if (lista[meio] < valor) {
      inicio = meio + 1;
    } else {
      fim = meio - 1;
    }
  }
  return -1; // Retorna -1 se o valor não for encontrado
}

void main() {
  List<int> lista = [10, 20, 30, 40, 50];
  int posicao = pesquisaBinaria(lista, 40);
  print(posicao); // Saída: 3
}
```

### Ordenação por Seleção (Selection Sort)

O Selection Sort encontra o menor elemento e o coloca na posição correta a cada iteração.

```dart
void selectionSort(List<int> lista) {
  for (int i = 0; i < lista.length - 1; i++) {
    int menorIndice = i;
    for (int j = i + 1; j < lista.length; j++) {
      if (lista[j] < lista[menorIndice]) {
        menorIndice = j;
      }
    }
    int temp = lista[i];
    lista[i] = lista[menorIndice];
    lista[menorIndice] = temp;
  }
}

void main() {
  List<int> lista = [64, 25, 12, 22, 11];
  selectionSort(lista);
  print(lista); // Saída: [11, 12, 22, 25, 64]
}
```

### Ordenação por Inserção (Insertion Sort)

O Insertion Sort funciona construindo a lista em ordem, inserindo cada novo elemento na posição correta.

```dart
void insertionSort(List<int> lista) {
  for (int i = 1; i < lista.length; i++) {
    int chave = lista[i];
    int j = i - 1;

    while (j >= 0 && lista[j] > chave) {
      lista[j + 1] = lista[j];
      j--;
    }
    lista[j + 1] = chave;
  }
}

void main() {
  List<int> lista = [12, 11, 13, 5, 6];
  insertionSort(lista);
  print(lista); // Saída: [5, 6, 11, 12, 13]
}
```

### Fila (Queue)

Uma fila (`Queue`) é uma estrutura de dados FIFO (first-in, first-out).

```dart
import 'dart:collection';

void main() {
  Queue<String> fila = Queue<String>();

  fila.addAll(['A', 'B', 'C']);
  print(fila); // Saída: {A, B, C}

  fila.removeFirst();
  print(fila); // Saída: {B, C}
}
```

### Pilha (Stack)

Uma pilha pode ser implementada usando uma lista em Dart. É uma estrutura LIFO (last-in, first-out).

```dart
class Pilha<T> {
  List<T> _pilha = [];

  void push(T elemento) => _pilha.add(elemento);

  T pop() => _pilha.removeLast();

  T top() => _pilha.last;

  bool isEmpty() => _pilha.isEmpty;
}

void main() {
  var pilha = Pilha<int>();

  pilha.push(1);
  pilha.push(2);
  pilha.push(3);

  print(pilha.pop()); // Saída: 3
  print(pilha.top()); // Saída: 2
  print(pilha.isEmpty()); // Saída: false
}
```

### Algoritmo de Fatorial Recursivo

O fatorial de um número é o produto de todos os inteiros positivos até esse número. Este exemplo utiliza recursão.

```dart
int fatorial(int n) {
  if (n <= 1) return 1;
  return n * fatorial(n - 1);
}

void main() {
  print(fatorial(5)); // Saída: 120
}
```

### Algoritmo de Fibonacci Recursivo

A sequência de Fibonacci é uma série de números onde cada número é a soma dos dois anteriores.

```dart
int fibonacci(int n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

void main() {
  print(fibonacci(6)); // Saída: 8
}
```

Esses exemplos de estruturas de dados e algoritmos em Dart fornecem uma visão geral de como construir e manipular essas estruturas, além de como realizar operações comuns em listas, como busca e ordenação.
