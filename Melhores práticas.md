# Trade-offs

Devemos nos lembrar que sempre precisamos faze-los, nosso custo ou complexidade pode aumentar ou diminuir dependendo do que priorizar.

Exemplos do que podemos priorizar:
- Velocidade em enviar um produto ao mercado ao invés de custo
- Consistência, durabilidade e espaço em troca de performance

Aprenderemos sobre anti-patterns para evitarmos nas nossas soluções

# Habilitar escalabilidade

## Anti-pattern
Não habilitar escalabilidade nas camadas de sua aplicação de forma automática, tendo assim que aumentar os recursos de forma manual

## Best practice
Utilizar ferramentas de monitoramento para realizar o auto scaling baseado em X condição (I.E uso de cpu, ram, etc...)

# Automatizar o ambiente

## Anti-pattern

O administrador ter que configurar um ambiente cloud manualmente caso haja alguma falha na aplicação

## Best practice

- Cloudwatch detecta instâncias não íntegras
- EC2 auto scaling automaticamente inicia e configura um server idêntico 

# Tratar recursos como descartáveis

O cloud é uma ambiente de provisionamento automático, podemos criar e apagar instâncias sem medo a fim de reduzir custos em tempos de baixo tráfego

## Anti-pattern

- Com o passar do tempo, diversos servers são configurados diferentemente
- Recursos ligados mesmo quando não utilizados
- Endereços IPs codados prejudicam a flexibilidade
- Dificuldade de atualizar com o hardware em uso

## Best practice

- Automatizar o deploy de novas versões com configurações idênticas
- Apagar recursos que não estão em uso
- Alternar para novos endereços de ip automaticamente
- Testar atualizações em novos recursos e depois substituir os antigos pelos atualizados

# Baixo acoplamento

Se um dos dogmas da engenharia de software é ter baixo acoplamento entre implementações, por que faríamos o mesmo com nossa infra?

## Anti-pattern

Ter uma arquitetura onde certos recursos tem um acoplamento direto com algum outros recursos

## Best practice

Uma arquitetura abstraída, por exemplo bater em um api gateway para que algo que dependa de x serviço não tenha que fazer o "hard coding" de algo

# Projetar serviços, não servidores

## Anti-pattern

- Aplicações simples são sempre executadas em servidores persistentes
- Aplicações sempre se comunicam entre umas as outras
- Os arquivos estáticos da Web são armazenados localmente em instâncias
- Os servidores de back-end processam a autenticação de estado dos usuários

## Best practices
- Usar serverless ou containers
- Message queues processam a comunicação entre aplicações
- Ativos estáticos Web sempre armazenados em um S3
- O armazenamento do estado e autenticação dos usuários são processados por serviços gerenciados da AWS (discutível imo, gerenciar seu próprio auth não é tão complicado imho)

# Evitar pontos únicos de falha

Presuma que tudo falhará. Então faça a engenharia reversa do projeto

# Utilizar caching

É sempre melhor utilizar um caching para recuperar dados frequentemente acessados rapidamente, ao invés de ter que procura-los sempre que forem requeridos.










