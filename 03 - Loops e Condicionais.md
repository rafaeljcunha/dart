## Condicionais em Dart

### 1. `if` e `else`

Esses são os blocos de controle de fluxo mais comuns, usados para executar código condicionalmente.

```dart
void main() {
  int idade = 18;

  if (idade >= 18) {
    print('Você é maior de idade.');
  } else {
    print('Você é menor de idade.');
  }
}
```

### 2. `else if`

O `else if` permite testar várias condições em sequência.

```dart
void main() {
  int nota = 75;

  if (nota >= 90) {
    print('Aprovado com A');
  } else if (nota >= 80) {
    print('Aprovado com B');
  } else if (nota >= 70) {
    print('Aprovado com C');
  } else {
    print('Reprovado');
  }
}
```

### 3. Operador Ternário

O operador ternário (`condição ? valorSeVerdadeiro : valorSeFalso`) permite simplificar `if-else` em uma linha.

```dart
void main() {
  int numero = 10;
  String tipo = numero % 2 == 0 ? 'Par' : 'Ímpar';

  print('O número $numero é $tipo');
}
```

### 4. `switch` e `case`

O `switch` é útil para comparar uma variável com vários valores possíveis.

```dart
void main() {
  String dia = 'Segunda';

  switch (dia) {
    case 'Segunda':
      print('Início da semana');
      break;
    case 'Sábado':
    case 'Domingo':
      print('Fim de semana');
      break;
    default:
      print('Dia comum');
  }
}
```

## Loops em Dart

### 1. `for` Loop

O `for` loop é utilizado para repetir um bloco de código um número específico de vezes.

```dart
void main() {
  for (int i = 1; i <= 5; i++) {
    print('Contagem: $i');
  }
}
```

### 2. `for` Loop com Listas

É comum usar o `for` loop para iterar sobre listas.

```dart
void main() {
  List<String> frutas = ['Maçã', 'Banana', 'Laranja'];

  for (int i = 0; i < frutas.length; i++) {
    print(frutas[i]);
  }
}
```

### 3. `for-in` Loop

Dart também suporta o `for-in`, uma sintaxe simplificada para percorrer listas e coleções.

```dart
void main() {
  List<String> nomes = ['Alice', 'Bob', 'Charlie'];

  for (var nome in nomes) {
    print('Olá, $nome!');
  }
}
```

### 4. `forEach` com Funções Anônimas

Você também pode usar o método `forEach` com listas para aplicar uma função a cada item.

```dart
void main() {
  List<int> numeros = [1, 2, 3, 4, 5];

  numeros.forEach((numero) {
    print(numero * 2); // Dobra cada número
  });
}
```

### 5. `while` Loop

O `while` loop executa enquanto a condição é verdadeira.

```dart
void main() {
  int contador = 1;

  while (contador <= 5) {
    print('Contagem: $contador');
    contador++;
  }
}
```

### 6. `do-while` Loop

O `do-while` é semelhante ao `while`, mas garante que o bloco seja executado ao menos uma vez.

```dart
void main() {
  int contador = 1;

  do {
    print('Contagem: $contador');
    contador++;
  } while (contador <= 5);
}
```

### 7. Controle de Fluxo com `break` e `continue`

- **`break`**: Interrompe o loop imediatamente.
- **`continue`**: Pula a iteração atual e vai para a próxima.

```dart
void main() {
  // Exemplo com break
  for (int i = 1; i <= 5; i++) {
    if (i == 3) {
      break; // Interrompe o loop quando i é 3
    }
    print('Número: $i');
  }

  // Exemplo com continue
  for (int j = 1; j <= 5; j++) {
    if (j == 3) {
      continue; // Pula a iteração quando j é 3
    }
    print('Número: $j');
  }
}
```

### 8. Loops Aninhados

Você pode aninhar loops para criar estruturas de repetição mais complexas.

```dart
void main() {
  for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
      print('i: $i, j: $j');
    }
  }
}
```

## Exemplos Práticos

### Exemplo 1: Soma de Números Pares com `for` Loop

```dart
void main() {
  int soma = 0;

  for (int i = 0; i <= 10; i++) {
    if (i % 2 == 0) {
      soma += i;
    }
  }

  print('A soma dos números pares entre 0 e 10 é: $soma');
}
```

### Exemplo 2: Fatorial de um Número com `while` Loop

```dart
void main() {
  int numero = 5;
  int fatorial = 1;

  while (numero > 1) {
    fatorial *= numero;
    numero--;
  }

  print('Fatorial: $fatorial');
}
```

### Exemplo 3: Contagem de Ocorrências em uma Lista com `forEach`

```dart
void main() {
  List<String> palavras = ['Dart', 'Flutter', 'Dart', 'Mobile', 'Dart'];
  Map<String, int> contagem = {};

  palavras.forEach((palavra) {
    contagem[palavra] = (contagem[palavra] ?? 0) + 1;
  });

  print(contagem); // Saída: {Dart: 3, Flutter: 1, Mobile: 1}
}
```

Esses exemplos mostram várias maneiras de utilizar loops e condicionais em Dart. Eles são extremamente úteis em cenários de controle de fluxo, manipulação de listas e coleções, além de simplificar operações repetitivas no código.
