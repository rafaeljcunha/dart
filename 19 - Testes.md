### Testes de Unidade, Integração e Funcionais

#### Testes de Unidade

Testes de unidade verificam funcionalidades isoladas de uma aplicação. Usaremos o pacote `test`.

```dart
// my_calculator.dart
int soma(int a, int b) => a + b;
```

```dart
// test/my_calculator_test.dart
import 'package:test/test.dart';
import '../my_calculator.dart';

void main() {
  test('Deve retornar a soma de dois números', () {
    expect(soma(3, 2), equals(5));
  });
}
```

#### Testes de Integração

Os testes de integração verificam o funcionamento entre diferentes partes do código. Suponha que estamos testando um serviço de API.

```dart
// api_service.dart
class ApiService {
  Future<String> fetchData() async {
    await Future.delayed(Duration(seconds: 1));
    return "Dados recebidos!";
  }
}
```

```dart
// test/api_service_test.dart
import 'package:test/test.dart';
import '../api_service.dart';

void main() {
  final api = ApiService();

  test('fetchData deve retornar dados', () async {
    expect(await api.fetchData(), "Dados recebidos!");
  });
}
```

#### Testes Funcionais

São testes mais amplos que simulam a experiência do usuário final. Em Dart, para aplicativos Flutter, normalmente se utiliza o `flutter_test`.

---

### 3. Testes Assíncronos

```dart
import 'package:test/test.dart';

Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 1));
  return 'Dados carregados';
}

void main() {
  test('fetchData deve retornar dados', () async {
    expect(await fetchData(), equals('Dados carregados'));
  });
}
```
