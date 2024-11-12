## Nível Básico

1. **Calcular Média de Notas**  
   Crie uma função que receba uma lista de notas (números) e retorne a média dessas notas. Depois, imprima se a média é suficiente para aprovação (acima de 7.0).

2. **Conversor de Temperatura**  
   Escreva uma função que converta uma temperatura de Fahrenheit para Celsius. Receba a temperatura em Fahrenheit e retorne o valor convertido.

3. **Verificar Par ou Ímpar**  
   Crie uma função que receba um número inteiro e retorne se ele é par ou ímpar.

4. **Contar Números Positivos**  
   Dada uma lista de números, conte quantos números são positivos. Crie uma função que retorne essa contagem.

5. **Filtro de Lista**  
   Escreva uma função que receba uma lista de números e retorne apenas os números maiores que 10.

6. **Soma de Números Pares**  
   Crie uma função que receba uma lista de números e retorne a soma de todos os números pares da lista.

7. **Calcular Área do Retângulo**  
   Crie uma função que receba a largura e a altura de um retângulo e retorne sua área.

8. **Contador de Vogais**  
   Escreva uma função que receba uma string e conte quantas vogais ela contém.

9. **Gerar Lista de Quadrados**  
   Crie uma função que receba um número inteiro `n` e retorne uma lista contendo o quadrado dos números de 1 até `n`.

10. **Números Ímpares entre 1 e 100**  
    Use um loop `for` para imprimir todos os números ímpares entre 1 e 100.

---

## Nível Intermediário

1. **Classe para Produto**  
   Crie uma classe `Produto` com propriedades `nome`, `preço`, e `estoque`. Adicione um método que diminua o `estoque` quando uma quantidade for vendida.

2. **Função Recursiva para Sequência de Fibonacci**  
   Escreva uma função recursiva que retorne o `n`-ésimo número da sequência de Fibonacci.

3. **Função para Média com Nota Máxima e Mínima**  
   Crie uma função que receba uma lista de notas e calcule a média excluindo a nota mais baixa e a mais alta.

4. **Converter Lista para Mapa**  
   Dada uma lista de strings, converta-a em um mapa onde cada chave é uma string da lista e o valor é o comprimento dessa string.

5. **Lista de Produtos com Filtragem**  
   Dada uma lista de objetos `Produto`, crie uma função que retorne uma lista dos produtos com preço superior a 100.

6. **Gerador de Senha Aleatória**  
   Crie uma função que gere uma senha aleatória com letras, números e caracteres especiais.

7. **Contagem de Caracteres em String**  
   Escreva uma função que receba uma string e retorne um mapa com cada caractere como chave e o número de vezes que aparece na string.

8. **Classes com Construtores Nomeados**  
   Crie uma classe `Carro` com diferentes construtores nomeados para inicializar um `Carro` com características específicas, como `luxo` e `esportivo`.

9. **Ordenação de Lista de Mapas**  
   Crie uma lista de mapas, onde cada mapa tem o nome e a idade de uma pessoa. Ordene essa lista pela idade.

10. **Função para Identificar Palíndromo**  
    Crie uma função que receba uma string e retorne se ela é um palíndromo (lê-se da mesma forma de trás para frente).

---

## Nível Avançado

1. **Mixin para Registro de Log**  
   Crie um `mixin` que adicione uma função de log a qualquer classe que o implemente. A função de log deve imprimir uma mensagem formatada com a data e a mensagem passada.

2. **Extensão para Listas**  
   Crie uma extensão em `List` para adicionar um método que retorne uma nova lista contendo apenas os elementos únicos.

3. **Manipulação de Streams com Transformações**  
   Crie uma `Stream` que emita números de 1 a 20. Em seguida, transforme essa `Stream` para emitir o dobro de cada número e imprima os resultados.

4. **Implementação de Classe Singleton**  
   Crie uma classe `Configuracao` que permita apenas uma única instância (singleton) no programa. A classe deve armazenar configurações globais.

5. **Classe Abstrata e Implementação Concreta**  
   Crie uma classe abstrata `FormaGeometrica` com métodos para calcular a área e o perímetro. Implemente as classes concretas `Circulo` e `Retangulo`.

6. **Broadcast Stream**  
   Crie uma `Stream` do tipo broadcast para emitir uma lista de números de 1 a 10. Adicione dois ouvintes (listeners) para essa `Stream`, um que exiba o número e outro que exiba o dobro do número.

7. **Função Assíncrona que Retorna Vários Resultados**  
   Implemente uma função que use `await` em múltiplos `Future`s e retorne uma lista de resultados. Exemplo: buscar a previsão do tempo de três cidades diferentes.

8. **Serialização Complexa com JSON**  
   Crie uma classe `Pedido` com `id`, `cliente`, e uma lista de `Produtos`. Crie métodos para converter a classe `Pedido` em JSON e vice-versa.

9. **Implementação de Fila com Estrutura de Dados**  
   Implemente uma classe `Fila` com métodos para adicionar e remover itens, obedecendo o princípio FIFO (First In, First Out).

10. **Lidar com Exceções Customizadas**  
    Crie uma exceção personalizada `ErroSaldoInsuficiente`. Depois, crie uma função `sacar` em uma classe `Conta` que lance essa exceção se o saldo for insuficiente.

---

## Nível Especialista

1. **Árvore Binária de Busca**  
   Implemente uma árvore binária de busca com métodos para adicionar e buscar nós.

2. **Stream Completa com Filtros e Transformações**  
   Crie uma `Stream` que emita eventos de temperatura e adicione transformações para filtrar temperaturas acima de 30 graus e converter a escala para Fahrenheit.

3. **Sistema de Cache com Fábrica e Singleton**  
   Desenvolva uma classe `Cache` usando o padrão Singleton e adicione um `factory` para criar instâncias de cache para diferentes propósitos (ex: cache de imagens, cache de dados).

4. **Arquivo JSON com Várias Tabelas**  
   Implemente um programa que leia um arquivo JSON complexo contendo várias tabelas (ex: clientes, pedidos e produtos) e organize os dados em classes separadas.

5. **Alocação de Memória e Otimização**  
   Crie um código que adicione objetos repetidamente a uma lista e experimente otimizar a alocação de memória, garantindo que objetos desnecessários sejam removidos.

6. **API de Clima com Tratamento de Erros Avançado**  
   Crie uma classe que consuma uma API de clima e implemente tratamento de erros avançado para identificar problemas de rede e exibir mensagens específicas para cada erro.

7. **Implementação de Mapa e Reduzir Uso de Memória**  
   Crie uma estrutura de dados personalizada que funcione como um mapa, mas otimizada para reduzir o uso de memória, usando `WeakReference` ou técnicas similares.

8. **Operadores Avançados em Cálculos**  
   Crie uma função que faça uso de operadores de shift e bitwise para criptografar uma mensagem usando uma chave simples.

9. **Construção Modular com Classes Genéricas e Mixins**  
   Desenvolva um sistema de produtos que use generics e mixins para permitir diferentes tipos de produtos e estender funcionalidades específicas, como `ProdutoDigital` e `ProdutoFisico`.

10. **Implementar um Garbage Collector Personalizado para Objetos Antigos**  
    Simule um garbage collector que identifique objetos “antigos” não utilizados e os remova da memória manualmente, sem interferir no garbage collector do Dart.
