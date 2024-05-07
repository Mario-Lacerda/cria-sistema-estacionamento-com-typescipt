# **Desafio Dio - Sistema de Estacionamento usando TypeScript**



### **Criando um Sistema de Estacionamento**

Para criar um sistema de estacionamento usando TypeScript, você pode seguir estas etapas:

**TypeScript** é um superset de JavaScript que adiciona tipagem estática ao idioma. Isso significa que você pode definir tipos para suas variáveis e funções, o que pode ajudar a prevenir muitos tipos de erros comuns em tempo de compilação, antes mesmo de seu código ser executado.

Para começar, você precisará instalar o Node.js e o npm (Node Package Manager). Depois, instale o TypeScript globalmente usando o npm:

```
npm install -g typescript
```



#### **1. Estruturando o Projeto**

Estruture seu projeto em pastas e arquivos separados para manter o código organizado e fácil de navegar. Por exemplo, você pode ter as seguintes pastas:

- **models:** Para armazenar os modelos de dados
- **services:** Para armazenar os serviços de negócios
- **controllers:** Para armazenar os controladores de API
- **tests:** Para armazenar os testes unitários

#### **2. Documentando o Código**

Documente seu código usando comentários ou ferramentas de documentação como JSDoc ou TypeDoc. Isso ajudará outros desenvolvedores a entender o propósito e o uso de suas funções e classes.

#### **3. Definindo Modelos**

Defina os modelos de dados para seu sistema de estacionamento. Isso incluirá informações como o número da vaga, o tipo de veículo e a hora de entrada e saída.

typescript

```typescript
interface Estacionamento {
  numeroVaga: number;
  tipoVeiculo: string;
  horaEntrada: Date;
  horaSaida: Date;
}
```



#### **4. Definindo Serviços**

Crie serviços para encapsular a lógica de negócios. Por exemplo, você pode criar um serviço de estacionamento com métodos para estacionar e retirar veículos, calcular o valor do estacionamento, etc.



```typescript
class EstacionamentoService {
  estacionarVeiculo(numeroVaga: number, tipoVeiculo: string) { ... }
  retirarVeiculo(numeroVaga: number) { ... }
  calcularValorEstacionamento(numeroVaga: number, horaSaida: Date) { ... }
}
```

#### **5. Definindo Controladores**

Crie controladores para expor a funcionalidade do seu sistema de estacionamento por meio de uma API. Por exemplo, você pode criar um controlador de estacionamento com rotas para estacionar e retirar veículos, calcular o valor do estacionamento, etc.



```typescript
@Controller('/estacionamento')
class EstacionamentoController {
  @Post('/')
  estacionarVeiculo(@Body() estacionamento: Estacionamento) { ... }
  @Delete('/:numeroVaga')
  retirarVeiculo(@Param('numeroVaga') numeroVaga: number) { ... }
  @Get('/:numeroVaga/valor')
  calcularValorEstacionamento(@Param('numeroVaga') numeroVaga: number) { ... }
}
```

#### **6. Integrando e Testando**

Integre todos os componentes do seu sistema e escreva testes unitários para verificar se o sistema está funcionando conforme o esperado.



#### **Definir o Modelo de Dados**

Comece definindo o modelo de dados para seu sistema de estacionamento. Isso incluirá informações como o número da vaga, o tipo de veículo e a hora de entrada e saída.

typescript

```typescript
interface Estacionamento {
  numeroVaga: number;
  tipoVeiculo: string;
  horaEntrada: Date;
  horaSaida: Date;
}
```

#### **Criar um Array de Vagas**

Em seguida, crie um array para armazenar as vagas de estacionamento.

typescript

```typescript
const vagas: Estacionamento[] = [];
```

#### **Adicionar Vagas ao Array**

Você pode adicionar vagas ao array usando o método `push()`.

typescript

```typescript
vagas.push({
  numeroVaga: 1,
  tipoVeiculo: "Carro",
  horaEntrada: new Date(),
  horaSaida: null,
});
```

#### **Estacionar um Veículo**

Para estacionar um veículo, você pode criar uma função que receba o número da vaga e o tipo de veículo.

typescript

```typescript
function estacionarVeiculo(numeroVaga: number, tipoVeiculo: string) {
  // Verificar se a vaga está disponível
  const vaga = vagas.find(vaga => vaga.numeroVaga === numeroVaga);
  if (!vaga || vaga.horaSaida !== null) {
    throw new Error("Vaga indisponível");
  }

  // Atualizar a vaga
  vaga.tipoVeiculo = tipoVeiculo;
  vaga.horaEntrada = new Date();
}
```

#### **Retirar um Veículo**

Para retirar um veículo, você pode criar uma função que receba o número da vaga.

typescript

```typescript
function retirarVeiculo(numeroVaga: number) {
  // Verificar se o veículo está estacionado
  const vaga = vagas.find(vaga => vaga.numeroVaga === numeroVaga);
  if (!vaga || vaga.horaSaida !== null) {
    throw new Error("Veículo não estacionado");
  }

  // Atualizar a vaga
  vaga.horaSaida = new Date();
}
```

#### **Calcular o Valor do Estacionamento**

Para calcular o valor do estacionamento, você pode criar uma função que receba o número da vaga e a hora de saída.

typescript

```
function calcularValorEstacionamento(numeroVaga: number, horaSaida: Date) {
  // Verificar se o veículo está estacionado
  const vaga = vagas.find(vaga => vaga.numeroVaga === numeroVaga);
  if (!vaga || vaga.horaSaida !== null) {
    throw new Error("Veículo não estacionado");
  }

  // Calcular a diferença entre a hora de saída e a hora de entrada
  const diferencaHoras = (horaSaida.getTime() - vaga.horaEntrada.getTime()) / (1000 * 60 * 60);

  // Calcular o valor do estacionamento com base na tarifa horária
  const tarifaHoraria = 5; // Valor de exemplo
  const valorEstacionamento = diferencaHoras * tarifaHoraria;

  return valorEstacionamento;
}
```

## **Conclusão**

Seguindo essas etapas, você pode criar um sistema de estacionamento robusto e bem projetado usando TypeScript. A tipagem estática do TypeScript pode ajudar a garantir que seu código seja preciso e fácil de manter. Além disso, estruturar seu projeto, documentar seu código e escrever testes unitários ajudará a melhorar a qualidade e a confiabilidade do seu sistema.

### **Aprendizado e Aplicabilidade Prática**

Desenvolver um sistema de estacionamento usando TypeScript pode ser uma ótima maneira de aprender sobre os seguintes conceitos:

- Tipagem estática
- Modelagem de dados
- Lógica de negócios
- Desenvolvimento orientado a testes
- Integração de sistemas

Esses conceitos são amplamente aplicáveis no desenvolvimento de software e podem ser usados em uma variedade de projetos do mundo real.
