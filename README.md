# Desenvolvimento de Métricas Customizadas em .NET

Este documento descreve a implementação de métricas customizadas usando a plataforma .NET, uma estratégia essencial para monitorar a performance e a operação de aplicações em tempo real. Este projeto foi desenvolvido seguindo as diretrizes do tutorial oficial da Microsoft para instrumentação de métricas, com foco na métrica específica de número de vendas de chapéus para uma loja fictícia, a HatCo.

## Requisitos Necessários
Para a realização deste projeto, é necessário:
- Instalação do [.NET 8](https://dotnet.microsoft.com/pt-br/download/dotnet/8.0)
- Uso do ambiente de desenvolvimento [JetBrains Rider](https://www.jetbrains.com/pt-br/rider/)
- Instalação do `dotnet-counters` via comando:
  ```bash
  dotnet tool install --global dotnet-counters
  ```

## Tecnologias Empregadas
- **.NET SDK 8:** Utilizado para desenvolver aplicações em .NET.
- **Rider:** IDE da JetBrains adaptado para desenvolvimento em .NET, suportando múltiplos frameworks e linguagens.
- **cURL:** Ferramenta CLI utilizada para transferir dados utilizando URLs.

## Criação de uma Métrica Personalizada

### 1. Início com Console Application
Inicialização de um projeto de aplicativo de console com .NET 8, configurado para suportar a coleta de métricas.
```
dotnet run
```

### 2. Configuração Inicial
No projeto criado, incluímos o pacote NuGet `System.Diagnostics.DiagnosticSource` para permitir a geração de métricas e fontes de diagnóstico.

### 3. Codificação das Métricas

```csharp
using System.Diagnostics.Metrics;

class Program
{
    static Meter s_meter = new Meter("HatCo.Store");
    static Counter<int> s_hatsSold = s_meter.CreateCounter<int>("hatc0.store.hats_sold");

    static void Main()
    {
        Thread.Sleep(1000);
        s_hatsSold.Add(1);
    }
}
```



![evidencia](./assets/2024-05-1109.04.09.jpeg)

