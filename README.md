# READMEMLABS

# MLabs – Sistema de Gestão de Amostras Celulares para Laboratórios
Descrição do Projeto
MLabs é um sistema LIMS (Laboratory Information Management System) para controle de amostras celulares em laboratórios de pesquisa, viabilizando a rastreabilidade completa desde o armazenamento físico (freezers, racks, caixas, frascos) até o registro individual de células, pesquisadores e ações sensíveis. O sistema permite a gestão de usuários, amostras, controle de movimentações e auditoria das ações realizadas no laboratório.

# Modelagem de Dados e Lógica de Negócio
O sistema implementa uma hierarquia física conforme o diagrama abaixo:

Freezer: Armazenamento principal, com tipos/capacidade.

Rack: Estrutura intermediária, organizada dentro do freezer.

Box (Caixa): Local de armazenamento de frascos, contido no rack.

Vial (Frasco): Unidade onde células são armazenadas (até 100 por caixa).

Cell (Célula): Registrada por tipo, clone, passage, datas, autor de pesquisa.

User (Usuário): Permite perfis (admin, gerente, pesquisador), acesso, autenticação.

O relacionamento segue o fluxo físico do laboratório:
Freezer → Rack → Caixa → Frasco → Célula

# A modelagem suporta:

Auditoria via SensitiveAccessLog

Tipagem/classificação detalhada (CellType)

Registro de pesquisas, testes, clones e logs por usuário responsável


# Requisitos Funcionais
O sistema contempla as seguintes ações:

Cadastro, visualização, atualização e remoção de usuários, freezers, racks, caixas, frascos e células

Autenticação segura de usuários

Fluxos administrativos e auditoria sensível das ações (alteração, replicação, retorno de frascos)

Exemplo de requisitos já implementados e planejados:

Cadastrar, visualizar, atualizar e remover cada item do laboratório (usuário, freezer, rack, caixa, frasco, célula)

Alterar senha, autenticar e gerenciar permissões

Auditoria de logs de acesso sensível


# Arquitetura do Sistema
MLabs é estruturado em módulos backend REST, garantindo desacoplamento, escalabilidade e fácil manutenção. A arquitetura segue o modelo:

Frontend (Web/App): Interface com usuário, envia requisições REST

LIMS API: Camada intermediária que recebe requisições, valida e direciona aos módulos

Authentication Module: Controle de usuários e permissões

Data Management Module: Gestão das entidades laboratoriais, armazenamento lógico

Workflow Management: Processa rotinas de rastreamento e movimentação de amostras

Reporting & Analytics: Gera relatórios, estatísticas e dashboards

Todas as operações são persistidas em banco PostgreSQL conforme o diagrama de entidades.


# Migrações (Migrations)
Migrações já implementadas
Banco de dados modelado com entidades para freezer, rack, box, vial, cell, user, celltype e logs

Scripts de criação de tabelas, relacionamento (FKs), constraints e enums para roles/metadados

Migrações para adicionar campos de auditoria de ação sensível

# Migrações futuras previstas
Refino de entidades para melhor rastreabilidade de clones (1:N)

Unificação ou expansão de repositórios conforme necessidades laboratoriais

Expansão da tabela de logs para rastrear novos métodos e níveis de permissão

Inclusão de tabelas auxiliares para integração futura com outros laboratórios/parceiros

# Identidade Visual
High and Low Contrast
<img width="2675" height="2160" alt="image" src="https://github.com/user-attachments/assets/f8c89746-4e0d-41cc-8032-c45364e1bbcc" />
<img width="2675" height="2160" alt="image" src="https://github.com/user-attachments/assets/5c108601-c80f-4189-9adc-99dda5c8a17a" />
<img width="6010" height="2028" alt="image" src="https://github.com/user-attachments/assets/e436c2f5-61ee-4b1e-98db-0786a6ed9f5c" />

# Mockup da Tela Inicial de Login
O mockup apresentado nesta proposta tem caráter inicial e serve para comunicar o conceito, estrutura básica e organização dos fluxos da plataforma. Durante a execução prevista no edital, serão conduzidas etapas de validação de usabilidade, testes com usuários e refinamento visual, resultando em telas de alta fidelidade e fluxo mais amadurecido, alinhados com as necessidades reais do laboratório e com padrões de design modernos. O layout final, cores, componentes e microinterações serão ajustados com base em validação contínua e feedback dos stakeholders do projeto, garantindo não só estética aprimorada, mas também uma experiência de uso eficiente e intuitiva
https://app.uizard.io/p/acd30ecf
![Tela de Login-Cadastro](https://github.com/user-attachments/assets/1bc7d4e6-060a-4c23-8ffb-ddb44db2bb75)
