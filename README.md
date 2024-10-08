# TeacherHunt

<p align="center" style='font-size: 25px'>
  API para gerenciamento de professores e aulas particulares
</p>

## Utilizar a API

- [Passo a passo para utilizar a api](./passo%20a%20passo%20uso%20da%20API.md)

## Descrição

Seu desafio é criar uma API para gerenciar professores e aulas particulares. A API deve permitir que professores se cadastrem e sejam listados, além de permitir que alunos busquem professores por descrição.

## Rotas

| Rota                                            | Método | Descrição                                                     | Requer Autenticação | Recursos fora do curso |
| ------------------------------------------      | ------ | ------------------------------------------------------------- | ------------------- |------------------------|
| /swagger/                                       |        | Documentação das rotas(acessar no navegador)                  | Não                 |  Adicionado            |
| /api/professores                                | GET    | Lista os professores                                          | Não                 |                        |
| /api/professores                                | POST   | Cadastra um professor                                         | Não                 |                        |
| /api/professores                                | PUT    | Atualiza os dados do professor logado                         | Sim                 |                        |
| /api/professores                                | DELETE | Exclui o professor logado                                     | Sim                 |                        |
| /api/professores/{professor_id}                 | GET    | Detalhes do professor                                         | Não                 |                        |
| /api/professores/foto                           | POST   | Atualiza a foto de um professor                               | Sim                 |                        |
| /api/professores/me                             | GET    | Detalhes do professor logado                                  | Sim                 |   Url modificada       |
| /api/professores/{materia_id}/materias          | GET    | Procura professor por Matéria(assunto)                        | Não                 |   Adicionado           |
| /api/professores/aulas                          | GET    | Lista as aulas e requisições de aula de um prof.              | Sim                 |   Adicionado           |
| /api/professores/aulas/{aula_id}                | GET    | Detalhes de uma aula                                          | Sim                 |   Adicionado           |
| /api/professores/aulas/aceitar/{aula_id}        | POST   | Aceita uma aula                                               | Sim                 |   Adicionado           |
| /api/professores/aulas/cancelar/{aula_id}       | POST   | Cancela uma aula                                              | Sim                 |   Adicionado           |
| /api/professores/{id_professor}/avaliacoes      | GET    | Lista todas as avaliações de um professor                     | Não                 |   Adicionado           |
| ------------------------------------------      |--------|-------------------------------------------------------------- |---------------------|------------------------|
| /api/alunos                                     | POST   | Cadastra um estudante                                         | Não                 |   Adicionado           |
| /api/alunos                                     | PUT    | Atuaiza os dados de um estudante logado                       | Sim                 |   Adicionado           |
| /api/alunos                                     | DELETE | Deleta um aluno logado                                        | Sim                 |   Adicionado           |
| /api/alunos/me                                  | GET    | Lista o aluno logado                                          | Sim                 |   Adicionado           |
| /api/alunos/foto                                | POST   | Atualiza a foto de um professor                               | Sim                 |   Adicionado           |
| /api/alunos/agendar-aulas                       | POST   | Cria uma requisição de aula                                   | Sim                 |   Adicionado           |
| /api/alunos/atualizar-aula/{aula_id}            | PUT    | Atualiza dados de uma aula                                    | Sim                 |   Adicionado           |
| /api/alunos/aulas                               | GET    | Lista as aulas de um aluno                                    | Sim                 |   Adicionado           |
| /api/alunos/aulas/{aula id}                     | GET    | Detalhes da aula                                              | Sim                 |   Adicionado           |
| /api/alunos/avaliar-professor                   | POST   | Avalia um professor                                           | Sim                 |   Adicionado           |
| /api/alunos/professores-favoritos               | GET    | Lista os professores favoritos de um aluno                    | Sim                 |   Adicionado           |
| /api/alunos/professores-favoritos/{professor_id}| POST   | Adiciona um professor da lista de favoritos                   | Sim                 |   Adicionado           |
| /api/alunos/professores-favoritos/{professor_id}| DELETE | Remove um professor da lista de favoritos                     | Sim                 |   Adicionado           |
| ------------------------------------------      |--------|-------------------------------------------------------------- |---------------------|------------------------|
| /api/materias                                   | GET    | Lista de todas as materias(subjects)                          | Não                 |   Adicionado           |
| /api/materias                                   | POST   | Cria uma nova materia(subject)                                | Sim(superuser)      |   Adicionado           |
| /api/materias                                   | DELETE | Deleta uma materia(subject)                                   | Sim(superuser)      |   Adicionado           |
| /api/materias                                   | PUT    | Atualiza completamente uma materia(subject)                   | Sim(superuser)      |   Adicionado           |
|-------------------------------------------      |--------|-------------------------------------------------------------- |---------------------|------------------------|
| /api/auth/login                                 | POST   | Faz login                                                     | Não                 |                        |
| /api/auth/refresh                               | POST   | Atualiza o token de acesso                                    | Não                 |                        |
| /api/auth/logout                                | POST   | Faz logout                                                    | Sim                 |                        |
| /api/auth/send-request-active-user              | POST   | Manda uma requisição com link de ativação da conta no email   | Não                 |   Adicionado           |
| /api/auth/active-user/{uidb64}/{token}          | GET    | Ativa a conta do usuário                                      | Não                 |   Adicionado           |
| /api/auth/password-reset-request                | POST   | Manda uma requisição com link de reset da password no email   | Não                 |   Adicionado           |
| /api/auth/password-reset/<uidb64>/<token>       | GET    | Checa se o token enviado é válido, retorna o token            | Não                 |   Adicionado           |
| /api/auth/password-reset-complete               | PATCH  | Redefine a senha passando o token e o uidb64                  | Não                 |   Adicionado           |
