# Arquitetura Escolha
## Story Telling 

A SportTec é uma empresa de venda de produtos esportivos.  

A empresa possui vários canais de venda por onde os clientes podem fazer as solicitações de compra. O cliente pode comprar roupas, tênis e outros itens esportivos.  

Existem clientes podem usar diversas plataformas para fazer a compra dos produtos. Podem usar nosso e-commerce, WhatsApp ou até nosso catálogo de produtos no Mercado Livre.  

Nossos analistas constantemente reclamam que precisam ficar gerenciando vários locais diferentes para entender se há um novo pedido para ser cobrado e entregue. 
Precisam ficar olhando a tela do WhatsApp, monitorar o e-mail com pedidos vindos do Mercado Livre, ficam atentos à plataforma do e-commerce para verificar se algo novo chega por lá também.  

Enfim, o desejo da área é que existisse um sistema centralizador que reunir-se todos os pedidos feitos independentemente da plataforma de onde foi feito. Com isso eles poderiam administrar melhor e não perderiam pedidos por confusões nessa logística. 


## O que esperamos aprender com esse projeto? 
- Implementação da estratégia de integração entre os sistemas de compra de pedidos visando uma centralização do gerenciamento da venda 

## Que perguntas precisamos que sejam respondidas? 
- Onde ficará esse sistema centralizador? 
- Quais são os canais que queremos consolidar? 
- Quantos pedidos são perdidos por não ter essa centralização? 
- Quais as funcionalidades deveriam ter nesse sistema? 
- O sistema funciona 24/7? 

## Quais são os nossos principais riscos? 
- Tentar automatizar e não ser efetivo 
- Impactar o processo de venda atual 
- Perder o pedido por erros nessa automatização 
- Correr risco com a imagem da companhia 
- Ter problemas com o estoque 

## Crie um plano para aprender o que precisamos para responder a perguntas específicas. 
- Vamos fazer entrevistas com o stakeholders para tentar entender se criaremos um sistema apartado ou se eles utilizam alguma ferramenta para gerenciar isso, um CRM ou planilhas. 
- Levantaremos informações sobre o funcionamento e o processo de venda em cada sistema, a criticidade e volumetria de cada plataforma.  
- Criaremos um plano de rollout e custos e prazo para o desenvolvimento dessa integração.  
- Fazer uma pesquisa de mercado e avaliar como nossos concorrentes resolvem o mesmo problema. 

## Crie um plano para reduzir riscos. 
- Treinamentos com a equipe para usarem o sistema novo 
- Criar um plano de rollout para mitigar problemas de integração com cada plataforma 
- Ter um período de testes e convivência/adaptação para o novo sistema 

## Quem são as partes interessadas? 
- Analistas da operação 
- Vendedores 
- Gerentes 
- Produtos 
- Marketing 
- Acionistas (por acrescer as vendas) 

## O que eles esperam ganhar? 
- Centralização dos pedidos de compra para facilitar a gestão 
- Visão do que está sendo vendido em cada plataforma 

## Redução do erro humano 
- Aumentar o número de canais de venda 

## Quem são os usuários? 
- Analistas de operação 
- Vendedores 
- Gerentes 

## O que eles estão tentando realizar? 
- Estão tentando realizar a gestão centralizada das vendas 

## Qual o pior que pode acontecer? 
- Perder venda por que o sistema ficou indisponível 

# Arquitetura Freeform
![Arquitetura de Aplicacao-SportTec drawio](https://github.com/user-attachments/assets/9b6d3e3d-a700-4454-aeea-77c208e477f1)

## Faça uma descrição de cada um dos componentes que você desenhou 

- Implementamos um firewall para proteger as requisições 
- Após isso temos um Api Gateway para fazer o direcionamento das requisições 
- O Api Gateway fará uma integração com um autenticador para fazer a identificação do usuário 
- O sistema unificado onde os nossos operadores podem avaliar os pedidos vindos das plataformas 
- O sistema unificado tem uma api e um banco de dados para fazer a gestão da operação de pedidos 
- O unificador é um artefato que vai buscar os pedidos nas diferentes plataformas (WhatsApp, Mercado Livre, E-Commerce)

## Descreva requisitos que você (s) considera importante e por quê? (Mínimo 5) 

- A disponibilidade do sistema é importante por que a venda ficar indisponível é ruim para a empresa 
- Latência, tempo de reposta e performance é importante por que o cliente pode desistir da compra pôr o sistema estar lento 
- Integridade do estoque dos produtos para não vender produto que não tem estoque 
- Escalabilidade da solução para casos de novos parceiros ou uma quantidade alta de pedidos para serem processados por dia. 
- Visibilidade dos dados de pedido. É importante termos um dashboard ou BI para analisar os pedidos que entram para estudos e estratégias de negócio.

## Sobre o que o diagrama ajuda você a raciocinar/pensar? 

- O modelo freeform ajuda a ver o fluxo da informação e a interligação entre os sistemas. 
- Ajuda a ter uma visão total de nossos componentes e pontos de falha.

## Quais são os padrões essenciais no diagrama? 
- Microserviços
- Autenticação 
- Responsabilidade única 

## Existem padrões ocultos? 
- Não

## Qual é o Metamodelo?	 
- O metamodelo é as regras que deixam o sistema independente dos outros e a integração com outros canais de venda. 

## Pode ser discernido no diagrama único? 
- Sim, no plano inicial do projeto conseguimos colocar todos os elementos em um diagrama apenas. 

## O diagrama está completo? 
- Para o início de nosso projeto sim, mas pode ser que no andar do desenvolvimento possa surgir mais alguns elementos. 

## Poderia ser simplificado e ainda assim ser eficaz? 
- Sim, remover o unificador e fazer a junção dos produtos com o próprio sistema poderia ficar mais simples, mas mais difícil de gerenciar. 

## Houve alguma discussão importante que vocês tiveram como equipe? 
- A discussão mais importante foi que como o sistema agora é automatizado, devemos tomar cuidado para não perder o pedido caso essa integração falhe. 

## Que decisões sua equipe teve dificuldade para tomar? 
- Como resolveríamos o problema da unificação dos sistemas. 

## Que decisões foram tomadas sob incerteza? 
- Se os parceiros externos possuem apis que poderiam ser consultadas. 

## Houve algum ponto de decisão sem retorno que o forçou a desistir de uma determinada escolha? 
- Não 

# Arquitetura C4 do Sistema 

## Nível Contexto 
![Arquitetura de Aplicacao-SportTec C4 - Contexto drawio](https://github.com/user-attachments/assets/e91abef9-b4dc-46e6-b499-c908cb8a63d8)

## Nível Container
![Arquitetura de Aplicacao-SportTec C4 - Container drawio](https://github.com/user-attachments/assets/4351cbf8-e76c-407c-b3c2-a0eb6a18bfc3)

## Nivel Componente: Api Central
![Arquitetura de Aplicacao-Copy of SportTec C4 - Component drawio](https://github.com/user-attachments/assets/d6c8151e-a797-45ac-9eae-20691c8444af)

## Nível Componente: Serviço de Sincronia
![Arquitetura de Aplicacao-Copy of SportTec C4 - Component drawio (1)](https://github.com/user-attachments/assets/9fc29c2c-aee0-458a-8ab3-ff4b7d756379)
