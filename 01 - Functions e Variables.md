## Variáveis em Dart

### 1. Declaração de Variáveis

Em Dart, você pode declarar variáveis usando `var`, `final`, ou `const`, e também especificar tipos explícitos.

- **`var`**: O tipo é inferido com base no valor atribuído. A variável pode ser alterada posteriormente.
- **`final`**: O valor não pode ser alterado após ser definido (imutável).
- **`const`**: O valor é constante em tempo de compilação e não pode ser alterado.

```dart
void main() {
  var nome = 'Rafael'; // Tipo inferido como String
  int idade = 30; // Tipo explicitamente definido como int
  final double altura = 1.75; // Valor imutável, definido uma única vez
  const PI = 3.14159; // Constante em tempo de compilação

  print('Nome: $nome, Idade: $idade, Altura: $altura, PI: $PI');
}
```

### 2. Tipos de Variáveis

Dart tem tipos básicos como `int`, `double`, `String`, `bool`, e `List`. Vamos ver alguns exemplos:

```dart
void main() {
  int ano = 2023;
  double preco = 29.99;
  String saudacao = 'Olá, mundo!';
  bool isAtivo = true;

  List<String> frutas = ['Maçã', 'Banana', 'Laranja'];

  print('Ano: $ano');
  print('Preço: $preco');
  print('Saudação: $saudacao');
  print('Ativo: $isAtivo');
  print('Frutas: $frutas');
}
```

### 3. Variáveis Nulas e Non-nullable

Em Dart, variáveis podem ser marcadas como nulas ou não-nulas. Para permitir que uma variável seja `null`, você usa o operador `?`.

```dart
void main() {
  int? numeroOpcional; // Pode ser null
  numeroOpcional = 42;

  print(numeroOpcional); // 42

  numeroOpcional = null;
  print(numeroOpcional); // null
}
```

## Funções em Dart

### 1. Funções Simples

Uma função simples em Dart é declarada com a palavra-chave `void` (caso não retorne nada) ou com um tipo de retorno específico.

```dart
void saudacao() {
  print('Olá, bem-vindo!');
}

int somar(int a, int b) {
  return a + b;
}

void main() {
  saudacao();

  int resultado = somar(3, 7);
  print('Resultado da soma: $resultado'); // Resultado da soma: 10
}
```

### 2. Funções com Parâmetros Nomeados e Opcionais

Dart permite definir parâmetros **nomeados** e **opcionais** para tornar as funções mais flexíveis.

- **Parâmetros nomeados**: Envolvem o parâmetro entre `{}`. Eles são opcionais por padrão.
- **Parâmetros opcionais posicionais**: Envolvem o parâmetro entre `[]`.

```dart
void mostrarMensagem({String? remetente, String mensagem = 'Olá'}) {
  print('Mensagem de $remetente: $mensagem');
}

void saudacao(String nome, [String? cumprimento]) {
  if (cumprimento != null) {
    print('$cumprimento, $nome!');
  } else {
    print('Olá, $nome!');
  }
}

void main() {
  mostrarMensagem(remetente: 'Rafael', mensagem: 'Bem-vindo ao Dart');
  mostrarMensagem(mensagem: 'Mensagem sem remetente');

  saudacao('Alice');
  saudacao('Bob', 'Bom dia');
}
```

### 3. Funções Anônimas e Arrow Functions

Funções anônimas não têm nome e são úteis para funções curtas. **Arrow functions** (funções flecha) são uma maneira concisa de definir funções de uma linha.

```dart
void main() {
  // Função anônima
  var nomes = ['Ana', 'Bruno', 'Carlos'];
  nomes.forEach((nome) {
    print('Olá, $nome!');
  });

  // Arrow function
  int dobrar(int numero) => numero * 2;

  print(dobrar(5)); // 10
}
```

### 4. Funções como Primeira Classe

Em Dart, funções são "primeira classe", o que significa que você pode atribuí-las a variáveis, passá-las como parâmetros e retorná-las de outras funções.

```dart
void saudarPessoa(String nome, Function estiloSaudacao) {
  estiloSaudacao(nome);
}

void estiloFormal(String nome) {
  print('Boa tarde, Sr(a). $nome.');
}

void estiloCasual(String nome) {
  print('Oi $nome!');
}

void main() {
  saudarPessoa('Maria', estiloFormal);
  saudarPessoa('João', estiloCasual);
}
```

### 5. Closures

Closures em Dart são funções que capturam variáveis do escopo onde foram definidas. Isso permite que a função tenha acesso a essas variáveis mesmo fora do escopo original.

```dart
Function contador() {
  int contagem = 0;

  return () {
    contagem++;
    print('Contagem: $contagem');
  };
}

void main() {
  var contar = contador();
  contar(); // Contagem: 1
  contar(); // Contagem: 2
}
```

### 6. Funções Assíncronas

Funções assíncronas em Dart utilizam `async` e `await` para operações assíncronas, como esperar por dados de uma API.

```dart
Future<String> buscarDados() async {
  await Future.delayed(Duration(seconds: 2));
  return 'Dados recebidos';
}

void main() async {
  print('Iniciando busca de dados...');

  String dados = await buscarDados();
  print(dados); // Dados recebidos
}
```

## Resumo Rápido

- **Variáveis**: Use `var` para variáveis mutáveis, `final` para variáveis imutáveis após serem definidas e `const` para valores constantes em tempo de compilação.
- **Funções**: Declare com tipos de retorno específicos, use parâmetros nomeados e opcionais para flexibilidade, e utilize `async` e `await` para operações assíncronas.
- **Closures e Funções como Primeira Classe**: Aproveite o poder das funções para criar código mais funcional e modular.

Esses são conceitos fundamentais de variáveis e funções em Dart que ajudam a estruturar e organizar o código de forma eficiente e legível.
