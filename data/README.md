# Base de Dados
Por meio dos arquivos Dumps (.sql) disponibilizado, os dados das tabelas foram carregados no MySQL, traduzidos e realizado a união destes dados em uma outra tabela criada, chamado: `dados_unidos` por meio dos relacionamentos das chaves: `person_id`, `loan_id`, `cb_id`.

Após realizar a união das tabelas, estes dados foram disponibilizados em 2 arquivos:
- `dados_juntos.csv` - União dos dados sem remoção de dados (Dados Brutos);
- `dados_tratados.csv` - União dos dados com remoção de dados nulos ou incompletos (Dados Tratados); 


## Dicionário de dados por tabela

### dados_mutuarios
Tabela contendo os dados pessoais de cada solicitante

| Feature (en) | Caracteristica (pt) | Tipo | Descrição |
| --- | --- | --- | --- |
|`person_id`| `id_usuario` | varchar(16) | ID da pessoa solicitante|
| `person_age` | `idade_usuario` | int | Idade da pessoa - em anos - que solicita empréstimo |
| `person_income` | `salario_usuario` | int | Salário anual da pessoa solicitante |
| `person_home_ownership` | `situacao_moradia_usuario` | varchar(10) | Situação da propriedade que a pessoa possui: *Alugada* (`Rent`), *Própria* (`Own`), *Hipotecada* (`Mortgage`) e *Outros* (`Other`) |
| `person_emp_length` | `tempo_de_trabalho_usuario` | double | Tempo - em anos - que a pessoa trabalhou |


### emprestimos
Tabela contendo as informações do empréstimos solicitados

| Feature (en) | Caracteristica (pt) | Tipo | Descrição |
| --- | --- | --- | --- |
|`loan_id`| `id_emprestimo` | varchar(16) | ID da solicitação de empréstico de cada solicitante|
| `loan_intent` | `motivo_emprestimo` | varchar(32) | Motivo do empréstimo: *Pessoal* (`Personal`), *Educativo* (`Education`), *Médico* (`Medical`), *Empreendimento* (`Venture`), *Melhoria do lar* (`Homeimprovement`), *Pagamento de débitos* (`Debtconsolidation`) |
| `loan_grade` | `pontuacao_emprestimo` | varchar(1) | Pontuação de empréstimos, por nível variando de `A` a `G` |
| `loan_amnt` | `valor_emprestimo` | int | Valor total do empréstimo solicitado |
| `loan_int_rate` | `taxa_juros_emprestimo` | double |  Taxa de juros do Emprestímo|
| `loan_status` | `status_emprestimo` | int | Status do Empréstimo ( Inadimplentes = 1 / Não-Inadimplentes= 0) |
| `loan_percent_income` | `renda_percentual_emprestimo` | double |  Renda percentual entre o *valor total do empréstimo* e o *salário anual* |


### historicos_banco
Histório de emprétimos de cada cliente

| Feature (en) | Caracteristica (pt) | Tipo | Descrição |
| --- | --- | --- | --- |
|`cb_id`| `id_hist_banco` | varchar(16) | ID do histórico de cada solicitante|
| `cb_person_default_on_file` | `devendo` | varchar(1) |  Indica se a pessoa já foi inadimplente: sim (`Y`,`YES`) e não (`N`,`NO`) |
| `cb_person_cred_hist_length` | `tempo_de_credito` |  int | Tempo - em anos - desde a primeira solicitação de crédito ou aquisição de um cartão de crédito |


### ids
Tabela que relaciona os IDs de cada informação da pessoa solicitante

| Feature (en) | Caracteristica (pt) | Tipo | Descrição |
| --- | --- | --- | --- |
|`person_id`| `id_usuario`|  varchar(16) | ID da pessoa solicitante|
|`loan_id`| `id_emprestimo`|  varchar(16) | ID da solicitação de empréstico de cada solicitante|
|`cb_id`| `id_hist_banco`|  varchar(16) | ID do histórico de cada solicitante|




