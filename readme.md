# A Evolução da Arquitetura de Software

A arquitetura de software é a estrutura principal de um sistema, definindo a organização dos componentes, sua comunicação e as regras que guiam sua evolução. O grande desafio é decompor sistemas em módulos com responsabilidades bem definidas.

---

## 1. Primeiras Arquiteturas e a Era do Monolito

### Era do Mainframe
- Sistemas centralizados e monolíticos  
- Programas, banco de dados e arquivos rodavam em uma única máquina poderosa  
- Acesso por "terminais burros"

### Cliente-Servidor (2 Camadas)
- Cliente instala um executável com lógica de negócio  
- Conexão direta ao banco de dados  
- Atualizações exigem reinstalação em todas as máquinas  
- Alta dificuldade de manutenção  

### Cliente-Servidor (3 Camadas)
- Introdução do Servidor de Aplicação  
- Cliente contém apenas a interface (UI)  
- Regras de negócio centralizadas no servidor intermediário  
- Dados mantidos no banco  
- Melhor centralização e manutenção  

### Cliente-Servidor (4 Camadas Web)
- Interface acessada via navegador (HTML, CSS, JS)  
- Introdução do Servidor Web  
- Elimina instalação no cliente  
- Reduz custos operacionais  
- Melhor desacoplamento  

---

## 2. Estilos Arquiteturais vs. Padrões Arquiteturais

### Estilos Arquiteturais
Definem a estrutura macro do sistema:
- Monolítico  
- Cliente-Servidor  
- Microserviços  
- Orientado a Eventos  

### Padrões Arquiteturais
Organizam responsabilidades dentro de um estilo:
- MVC  
- Clean Architecture  
- Hexagonal  

---

## 3. O Padrão MVC e Seus Limites

### MVC (Model-View-Controller)
Divide a aplicação em:
- **Model** → Manipula dados  
- **View** → Exibe a interface  
- **Controller** → Recebe requisições e coordena respostas  

### Limitações
- Forte acoplamento entre camadas  
- Dificuldade de reuso  
- Regras de negócio misturadas nos controllers  
- Dificuldade para testes automatizados  

---

## 4. Princípios de Design e Qualidade de Código

### Alta Coesão e Baixo Acoplamento
- Cada módulo deve ter uma responsabilidade clara  
- Dependências devem ser minimizadas  

### Princípios SOLID e TDD
- **S** → Responsabilidade Única  
- **D** → Inversão de Dependência  
- **TDD** → Desenvolvimento guiado por testes  
- Código mais desacoplado, testável e confiável  

---

## 5. Arquiteturas Modernas e Desacopladas

### Arquitetura de 4 Camadas Lógicas
Camadas:
1. Apresentação  
2. Aplicação  
3. Domínio  
4. Infraestrutura  

- Uso de Inversão de Dependência  
- Infraestrutura depende do domínio (não o contrário)  
- Uso de interfaces para desacoplamento  

### Arquitetura Hexagonal (Ports and Adapters)
- Núcleo isolado (regras e casos de uso)  
- Comunicação via:
  - **Portas** (interfaces)
  - **Adaptadores** (REST, banco de dados etc.)  
- Facilita testes e troca de tecnologias  

### Clean Architecture
Estrutura em círculos concêntricos:
- Entidades  
- Casos de Uso  
- Adaptadores de Interface  
- Frameworks  

**Regra de Dependência:**  
O código sempre aponta para o centro (núcleo do domínio), protegendo as regras de negócio da obsolescência tecnológica.

---

## 6. Infraestrutura e Arquitetura de Produção

### Primeiro Deploy
- Padronização de ambiente (Docker)  
- Hospedagem (VPS)  
- Proxy reverso / servidor web (Nginx)  

### Sistemas Corporativos
- Load Balancers → Distribuição de carga  
- API Gateways → Porta de entrada única  
- Cache (Redis) → Respostas rápidas  
- Batch Workers → Processamento em lote  

---

## 7. Escalabilidade e Sistemas Distribuídos

### Microserviços
- Serviços autônomos por domínio de negócio  
- Banco de dados próprio por serviço  
- Escalabilidade horizontal independente  

### Comunicação entre Serviços

#### APIs REST
- Comunicação síncrona simples  
- Pode gerar lentidão se um serviço falhar  

#### GraphQL
- Cliente solicita apenas os dados necessários  
- Evita overfetching e underfetching  
- Maior complexidade no backend  

#### Assíncrona e Event-Driven (Pub/Sub)
- Uso de Message Brokers (RabbitMQ, Kafka)  
- Serviços publicam eventos em filas  
- Consumidores processam de forma independente  
- Maior resiliência  

### SOA (Service-Oriented Architecture)
- Ideal para ambientes corporativos  
- Serviços reutilizáveis  
- Integração via ESB  
- Excelente para integrar sistemas legados  
- Governança mais burocrática  

### CQRS (Command Query Responsibility Segregation)
- Separa:
  - Escrita (comandos com regras de negócio)  
  - Leitura (consultas otimizadas para performance)  

- Ideal para sistemas com alto volume de leitura e escritas complexas  

---

# Conclusão

A arquitetura não é baseada em ferramentas, mas em decisões e princípios sólidos.

Um sistema moderno deve ser:
- Modular  
- Reativo  
- Escalável  
- Resiliente  
- Bem organizado  