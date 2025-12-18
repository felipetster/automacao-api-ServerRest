#  ServeRest API Automation Project

Este projeto consiste em uma suíte de testes automatizados para a API [ServeRest](https://serverest.dev/), simulando o fluxo real de um e-commerce.

O objetivo foi validar a confiabilidade dos endpoints críticos (CRUD), a segurança (Autenticação JWT) e a integridade dos dados através de scripts em JavaScript.

##  Tecnologias Utilizadas
* **Postman:** Estruturação das requisições e suites de teste.
* **JavaScript:** Scripts de pré-request e testes (asserções).
* **Chai Assertion Library:** Validação de respostas (BDD Style).
* **Git/GitHub:** Versionamento do código.

##  Cenários Cobertos (End-to-End)
A coleção executa a seguinte sequência lógica automatizada:

1.  ** Criação de Usuário:** Registro com dados dinâmicos (evitando conflitos).
2.  ** Autenticação (Login):** Extração e tratamento de Token JWT para uso em rotas protegidas.
3.  ** Gestão de Produtos:**
    * **Cadastro:** Inserção de produto validando Status 201.
    * **Consulta:** Validação dos dados inseridos (GET).
    * **Atualização:** Edição de preço/descrição (PUT).
4.  **🛒 Fluxo de Compra:**
    * Simulação de adição de itens ao carrinho.
    * Conclusão da compra (limpeza do carrinho).
5.  ** Data Teardown:** Exclusão dos dados gerados (usuários/produtos) para não sujar a base.

## Como executar este projeto
Para rodar os testes na sua máquina:

1.  Baixe os arquivos `.json` deste repositório.
2.  Abra o Postman e clique em **Import**.
3.  Selecione os arquivos `Collection` e `Environment`.
4.  No canto superior direito, selecione o ambiente **ServeRest**.
5.  Clique em **Run Collection** para ver o relatório de execução.

---
 *Projeto desenvolvido por [Felipe Castro] como parte do portfólio de QA.*
