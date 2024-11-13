### Trabalhar com Arquivos e Sistema de Arquivos

Dart tem a biblioteca `dart:io` para operações de arquivo.

```dart
import 'dart:io';

void main() async {
  final file = File('exemplo.txt');

  // Escrever no arquivo
  await file.writeAsString('Olá, Dart!');

  // Ler do arquivo
  String contents = await file.readAsString();
  print(contents); // Saída: Olá, Dart!

  // Append no arquivo
  await file.writeAsString('\nMais uma linha.', mode: FileMode.append);
}
```
