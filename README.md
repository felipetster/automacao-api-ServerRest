#  ServeRest API Automation

Este projeto apresenta uma suíte de testes automatizados de API desenvolvida no Postman para a plataforma ServeRest, simulando o fluxo completo de um e-commerce.

O foco da automação é garantir a confiabilidade dos endpoints críticos, validar regras de negócio, segurança (autenticação JWT) e integridade dos dados ao longo de um fluxo End-to-End, do cadastro até a finalização da compra.

## Objetivos do Projeto

* Validar o comportamento funcional dos principais endpoints (CRUD)
* Garantir o correto funcionamento da autenticação via JWT
* Assegurar consistência e integridade dos dados entre requisições
* Simular um fluxo real de uso da API, reduzindo riscos antes de produção
* Demonstrar boas práticas de automação e organização de testes de API
  
##  Tecnologias Utilizadas
* **Postman:** Estruturação das requisições e suites de teste.
* **JavaScript:** Scripts de pré-request e testes (asserções).
* **Chai Assertion Library:** Validação de respostas (BDD Style).
* **Git/GitHub:** Versionamento do código.

##  Cenários Cobertos (End-to-End)
A coleção executa a seguinte sequência lógica automatizada:

1.  **Criação de Usuário:** Registro com dados dinâmicos (evitando conflitos).
2.  **Autenticação (Login):** Extração e tratamento de Token JWT para uso em rotas protegidas.
3.  **Gestão de Produtos:**
    * **Cadastro:** Inserção de produto validando Status 201.
    * **Consulta:** Validação dos dados inseridos (GET).
    * **Atualização:** Edição de preço/descrição (PUT).
4.  **Fluxo de Compra:**
    * Simulação de adição de itens ao carrinho.
    * Conclusão da compra (limpeza do carrinho).
5.  **Data Teardown:** Exclusão dos dados gerados (usuários/produtos) para não sujar a base.

## Exemplos de Scripts

Abaixo, alguns trechos da lógica desenvolvida na aba **Tests** para garantir robustez na automação.

### 1. Autenticação Inteligente (Login)
Script utilizado para capturar o Token JWT, remover o prefixo "Bearer" (para evitar duplicações) e armazená-lo automaticamente nas variáveis de ambiente.

```javascript
var jsonData = pm.response.json();

// validacao de login
pm.expect(jsonData.message).to.eql("Login realizado com sucesso");

// tratamento e armazenamento do token
if (jsonData.authorization) {
    // A API retorna "Bearer <token>", o split pega apenas o código
    var tokenLimpo = jsonData.authorization.split(' ')[1];
    pm.environment.set("token", tokenLimpo);
}
```
## Como executar este projeto
Para rodar os testes na sua máquina:
1.  Baixe os arquivos `.json` deste repositório.
2.  Abra o Postman e clique em **Import**.
3.  Selecione os arquivos `Collection` e `Environment`.
4.  No canto superior direito, selecione o ambiente **ServeRest**.
5.  Clique em **Run Collection** para ver o relatório de execução.

---
 *Projeto desenvolvido por [Felipe Castro] como parte do portfólio de QA.*
