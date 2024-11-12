## Nível Básico

Estes exercícios introduzem conceitos fundamentais, como variáveis, funções, loops e condicionais.

1. **Variáveis e Operadores Simples**  
   Declare variáveis para armazenar seu nome, idade e altura. Imprima uma frase que combine essas variáveis usando interpolação de strings.

2. **Função Simples**  
   Crie uma função `soma` que receba dois números inteiros e retorne a soma deles.

3. **Estrutura Condicional**  
   Escreva uma função que receba uma idade e retorne se a pessoa é maior de idade ou não (18 anos).

4. **Loop com `for`**  
   Imprima todos os números de 1 a 10 usando um loop `for`.

5. **Listas Simples**  
   Crie uma lista de nomes e imprima cada nome usando um loop `for`.

6. **Dicionários Básicos**  
   Crie um `Map` com o nome de três pessoas como chave e suas idades como valor. Imprima cada nome e idade.

7. **Funções Anônimas**  
   Use uma função anônima para imprimir a soma de dois números.

8. **Função Recursiva Básica**  
   Crie uma função recursiva que calcule o fatorial de um número.

9. **Casting de Tipo**  
   Converta um número em uma string e uma string em um número, e imprima o resultado.

10. **Null Safety**  
    Declare uma variável que pode ser `null`. Atribua um valor a ela e use o operador de coalescência nula (`??`) para garantir um valor padrão.

---

## Nível Intermediário

Estes exercícios envolvem orientação a objetos, manipulação de coleções e programação assíncrona.

1. **Classes e Objetos**  
   Crie uma classe `Pessoa` com propriedades `nome` e `idade`. Crie um método para exibir uma saudação.

2. **Encapsulamento**  
   Modifique a classe `Pessoa` para tornar a `idade` privada e crie um método para acessar e modificar a idade.

3. **Listas e Mapas**  
   Dada uma lista de números, crie um mapa onde cada número é a chave e seu quadrado é o valor.

4. **Loops e Condicionais Avançados**  
   Crie uma função que receba uma lista de números e retorne apenas os números pares.

5. **Função Assíncrona com `Future`**  
   Crie uma função assíncrona que simule a busca de dados e retorne uma string após 2 segundos.

6. **Programação Funcional com `map` e `where`**  
   Dada uma lista de números, use `map` para multiplicar cada número por 2 e `where` para filtrar os números pares.

7. **Enum e Switch**  
   Crie uma `enum` para representar os dias da semana e uma função que imprima se o dia é útil ou fim de semana.

8. **Future e Manipulação de Erros**  
   Crie um `Future` que pode lançar uma exceção e lide com a exceção usando `catchError`.

9. **Casting de Coleções**  
   Converta uma lista de números inteiros para uma lista de strings.

10. **Métodos Estáticos**  
    Adicione um método estático à classe `Pessoa` que conte quantos objetos `Pessoa` foram criados.

---

## Nível Avançado

Estes exercícios cobrem estrutura de dados complexa, operadores avançados e programação assíncrona.

1. **Herança e Polimorfismo**  
   Crie uma classe `Animal` com um método `falar`, e subclasse `Cachorro` e `Gato` que implementem `falar` de forma diferente.

2. **Classe com `factory` e Construtores Nomeados**  
   Crie uma classe `Usuario` com um `factory` que cria um `Usuario` padrão.

3. **Operador Ternário e Coalescência Nula**  
   Escreva uma função que receba um valor opcional e retorne "Vazio" se for `null`, usando o operador `??`.

4. **Coleções Não Modificáveis**  
   Crie uma lista imutável de números e tente modificá-la (deve gerar erro).

5. **Loop com Cascade Notation**  
   Crie uma classe `Conta` com um método `depositar`. Use `Cascade Notation` para adicionar valores a uma conta.

6. **Manipulação de JSON e Serialização**  
   Crie uma classe `Produto` e converta uma lista de objetos `Produto` para JSON e vice-versa.

7. **Uso Avançado de `Future` e `await`**  
   Crie duas funções assíncronas que dependem dos resultados uma da outra. Use `await` para sincronizá-las.

8. **Stream de Dados**  
   Crie uma `Stream` que emita números inteiros de 1 a 10 e um listener para imprimir cada número.

9. **Broadcast Stream**  
   Crie uma `Stream` do tipo broadcast e adicione dois ouvintes (listeners) para imprimir cada evento.

10. **Aplicando Garbage Collection**  
    Identifique um código que crie objetos sem necessidade e otimize-o para minimizar o uso de memória.

---

## Nível Especialista

Estes exercícios envolvem algoritmos complexos, integração de API, trabalho com arquivos e outros tópicos avançados.

1. **Algoritmo de Busca Binária**  
   Implemente o algoritmo de busca binária em uma lista ordenada.

2. **Estrutura de Dados Avançada**  
   Implemente uma árvore binária com métodos para inserir e percorrer.

3. **Mixin e Extensões**  
   Crie um `mixin` para adicionar um método `log` a qualquer classe e uma extensão para reverter strings.

4. **Manipulação de Arquivos**  
   Crie um programa que leia e escreva em um arquivo JSON. Cada linha do arquivo deve representar um objeto JSON.

5. **Integração com APIs**  
   Consuma uma API de clima, parseie o JSON e exiba informações de temperatura e condição.

6. **Programação Assíncrona com Stream Transformation**  
   Crie uma `Stream` que emita uma lista de números e transforme-os para calcular o quadrado.

7. **Lidar com Exceções e Erros de Rede**  
   Implemente uma chamada de API que trate erros de conexão, usando `try` e `catch`.

8. **Garbage Collection Manual e Análise de Memória**  
   Escreva um código que simule o uso de memória excessiva e otimize-o, garantindo que o garbage collector limpe objetos não utilizados.

9. **Operadores Avançados e Expressions**  
   Use o operador de cascata (`..`) em uma classe complexa que possui várias operações de manipulação de dados.

10. **Criar um Sistema Modular com Classes Fábricas**  
    Desenvolva um sistema de gerenciamento de produtos que use classes fábricas para criar objetos de diferentes tipos de produtos, como `Eletronico`, `Vestuario`, etc.
