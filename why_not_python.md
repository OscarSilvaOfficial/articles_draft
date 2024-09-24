# Por que não escolher Python?

Sei que de cara já vou comprar briga com uma galera, mas vamos lá, este título não é clickbait.

Atuei por 6 anos como desenvolvedor Python, focado em desenvolvimento web, então esta reflexão é baseada na minha experiência. E honestamente, acredito que a escolha de Python para criar sistemas **complexos** pode trazer muitos desafios.

### Desempenho e Escalabilidade Não São o Principal Problema

Vamos deixar claro logo de início: o foco aqui não é a discussão de performance ou escalabilidade. Na maioria das empresas em que você for trabalhar, problemas de performance dificilmente serão causados pela linguagem. É muito mais comum que sejam decorrentes de queries mal otimizadas, arquiteturas mal planejadas ou de uma comunicação ineficiente entre serviços.

> **Obs**: Claro que, se você está em um ambiente onde a performance é elevada ao extremo (por exemplo, no desenvolvimento de sistemas de alta frequência), a escolha da linguagem pode sim se tornar relevante.

Além disso, o argumento da sintaxe também não é um fator decisivo aqui. Python é indiscutivelmente fácil de ler e escrever, mas adicionar algumas linhas extras para definir uma variável, método ou classe em linguagens com tipagem estática não é um grande sacrifício. No fim das contas, leitura e escrita de código é questão de prática.

### O Problema Real: Tipagem Dinâmica em Sistemas Distribuídos

Agora vamos direto ao ponto: **em sistemas grandes, distribuídos e complexos, linguagens com tipagem dinâmica podem se tornar um problema sério**. E é aqui que minha crítica a Python entra em cena.

Em uma linguagem com tipagem estática, como TypeScript, Java ou Go, o processo de desenvolvimento em sistemas distribuídos tende a ser mais controlado. Quando você trabalha em microsserviços, por exemplo, o primeiro passo normalmente é verificar o contrato de comunicação entre os serviços, definindo com precisão quais dados estarão disponíveis e quais tipos de dado serão trocados. O compilador, então, garante que os tipos estão corretos, proporcionando segurança e previsibilidade.

No Python, a história é diferente. Como não há tipagem estática, você não tem a garantia de que o contrato entre os serviços está sendo cumprido. O resultado? Você acaba tendo que percorrer o código manualmente para entender as variáveis disponíveis, muitas vezes sem qualquer garantia de tipo ou formato.

Vou dar um exemplo prático: em um microsserviço, precisei implementar uma nova feature que dependia de um payload recebido de outro serviço. Em linguagens com tipagem estática, esse payload teria um formato bem definido, e eu poderia confiar que o que chegasse seria sempre daquele formato. Mas em Python, o payload poderia conter qualquer coisa. E isso gera uma série de complicações:

1. Primeiro, é necessário validar se o campo que você quer acessar realmente existe no payload.
2. Em seguida, você precisa validar o tipo do campo.
3. Se o tipo for diferente do esperado, mas ainda possível de ser convertido, será necessário realizar a conversão antes de usar.

Esse processo é repetido para **cada campo** que você precisa trabalhar, introduzindo complexidade e aumentando o risco de bugs em tempo de execução. Em linguagens com tipagem estática, esse tipo de problema é resolvido pelo compilador, que faz essas verificações automaticamente e evita surpresas desagradáveis.

### Manutenção a Longo Prazo

Outro ponto crucial é a manutenção de longo prazo. Em sistemas complexos e distribuídos, a manutenção contínua é uma realidade. À medida que mais e mais funcionalidades são adicionadas, o sistema cresce, e a falta de tipagem estática pode começar a cobrar seu preço. 

Com o tempo, você vai encontrar situações em que não se sabe mais exatamente quais dados estão circulando entre os serviços. A documentação pode não estar atualizada, e o código em Python se torna cada vez mais difícil de manter. A falta de garantias sobre o tipo dos dados significa que, a cada nova feature, será necessário revisar manualmente o código existente para garantir que tudo ainda funciona como esperado.

Por outro lado, em uma linguagem com tipagem estática, os contratos de comunicação entre os microsserviços estão definidos no código e validados pelo compilador. Isso não só reduz o tempo de debug e a quantidade de bugs em produção, como também torna o sistema muito mais fácil de expandir e manter a longo prazo.

### Conclusão

Python é, sem dúvida, uma linguagem poderosa e versátil, especialmente em áreas como ciência de dados, automação e desenvolvimento web. No entanto, quando falamos de sistemas distribuídos e **complexos**, a ausência de tipagem estática e a dificuldade de lidar com contratos de comunicação tornam o desenvolvimento e a manutenção muito mais complicados.

Linguagens com tipagem estática como Go, Rust e TypeScript oferecem vantagens claras nesse cenário, proporcionando mais segurança em tempo de compilação, melhor performance em concorrência e uma manutenção mais tranquila a longo prazo.

No final das contas, Python tem seu lugar no ecossistema, mas para arquiteturas distribuídas e complexas, optar por uma linguagem com tipagem estática pode economizar tempo, reduzir a dívida técnica e evitar muitas dores de cabeça no futuro.

> **obs**: Python foi a minha primeira linguagem de programação, e tenho extremo carinho até hoje por ela. Mas lembrando, **É APENAS UMA FERRAMENTA**
