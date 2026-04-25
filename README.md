# Sistema de Gerenciamento de Veículos 🚗🚛

Projeto em C++ que simula uma **frota de veículos** (carros de passeio e caminhões), calculando custos de manutenção com base na quilometragem.  
O sistema demonstra conceitos de **POO** como **herança, composição, polimorfismo e agregação**.

---

## 📂 Estrutura do Projeto

- **Veiculo.h / Veiculo.cpp** → Classe base `Veiculo`, que possui um `Motor` por composição.  
- **Motor.h / Motor.cpp** → Classe `Motor`, representando potência e tipo de combustível.  
- **CarroPasseio.h / CarroPasseio.cpp** → Especialização de `Veiculo`, com regra própria de manutenção.  
- **Caminhao.h / Caminhao.cpp** → Especialização de `Veiculo`, com regra própria de manutenção.  
- **GerenciadoraVeiculos.h / GerenciadoraVeiculos.cpp** → Classe responsável por gerenciar a frota e calcular custos.  
- **main.cpp** → Demonstração prática do sistema.

---

## 🚀 Funcionalidades

- **Composição**:  
  A classe `Veiculo` possui um `Motor`, criado e destruído junto com o veículo.

- **Herança**:  
  `CarroPasseio` e `Caminhao` herdam de `Veiculo`, cada um com sua própria implementação de `calcularManutencao()`.

- **Polimorfismo**:  
  O método `calcularManutencao()` é sobrescrito em cada tipo de veículo, permitindo cálculos diferentes.

- **Agregação**:  
  A classe `GerenciadoraVeiculos` mantém uma lista de veículos (`frota`), mas não é responsável por criá-los diretamente.

---

## 🛠️ Exemplos de Uso

No `main.cpp`:

```cpp
GerenciadoraVeiculos gestor;

CarroPasseio* carro = new CarroPasseio("ABC-1234", 10000);
Caminhao* caminhao = new Caminhao("XYZ-9876", 50000);

gestor.adicionarVeiculo(carro);
gestor.adicionarVeiculo(caminhao);

std::cout << "\n--- Relatorio de Manutencao ---" << std::endl;
gestor.exibirRelatorioManutencao();

std::cout << "Custo total da frota: R$ "
          << std::fixed << std::setprecision(2)
          << gestor.calcularCustoTotal() << std::endl;
```

Saída esperada:

```
--- Relatorio de Manutencao ---
Placa: ABC-1234 | Custo manutencao: R$ 5000.00
Placa: XYZ-9876 | Custo manutencao: R$ 75000.00
Custo total da frota: R$ 80000.00
```

---

## ⚙️ Como Compilar e Executar

No terminal:

```bash
g++ main.cpp Veiculo.cpp Motor.cpp CarroPasseio.cpp Caminhao.cpp GerenciadoraVeiculos.cpp -o frota
./frota
```

---

## 🎯 Objetivo Didático

Este projeto foi desenvolvido para **demonstrar conceitos fundamentais de POO em C++** aplicados a um cenário de **gestão de frota**.  
Ele pode ser usado como **material de estudo** para entender:
- Diferença entre composição e agregação
- Herança e especialização de classes
- Polimorfismo em métodos virtuais
- Gerenciamento de memória dinâmica em C++
