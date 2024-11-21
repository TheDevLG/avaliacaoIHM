# Sistema de Gerenciamento de Biblioteca

## Requisitos Funcionais

### [RF001] Empréstimo de Livro
**Descrição:** Permite que o usuário realize o empréstimo de livros disponíveis no acervo.  
**Atores:** Usuário, Sistema, Biblioteca.  
**Prioridade:** **Essencial**

#### Entradas e Pré-condições:
- O usuário deverá informar o código do livro e sua identificação pessoal (por exemplo, CPF).  
- O livro deverá estar disponível no sistema.

#### Saídas e Pós-condições:
- O sistema registra o empréstimo e atualiza o status do livro para "Emprestado".

#### Fluxo Normal:
1. O usuário informa ao sistema o código do livro desejado e sua identificação.
2. O sistema verifica a disponibilidade do livro no acervo.
3. O sistema exibe uma mensagem confirmando a disponibilidade e solicita a confirmação do empréstimo.
4. O usuário confirma o empréstimo.
5. O sistema registra o empréstimo, atualiza o status do livro para "Emprestado" e informa a data de devolução ao usuário.

#### Fluxo Excepcional 1 (Livro indisponível):
- Se o livro estiver emprestado, o sistema exibe uma mensagem informando a indisponibilidade e sugere realizar uma reserva.

---

### [RF002] Devolução de Livro
**Descrição:** Permite que o usuário devolva livros emprestados para a biblioteca.  
**Atores:** Usuário, Sistema, Biblioteca.  
**Prioridade:** **Essencial**

#### Entradas e Pré-condições:
- O usuário deverá informar o código do livro que deseja devolver.  
- O livro deverá estar em status "Emprestado".

#### Saídas e Pós-condições:
- O sistema registra a devolução e atualiza o status do livro para "Disponível".

#### Fluxo Normal:
1. O usuário informa ao sistema o código do livro que deseja devolver.
2. O sistema verifica se o livro está registrado como "Emprestado" para o usuário.
3. O sistema registra a devolução e atualiza o status do livro para "Disponível".
4. O sistema exibe uma mensagem de confirmação da devolução.

#### Fluxo Excepcional 1 (Livro não encontrado):
- Se o código do livro informado não for encontrado ou não estiver emprestado, o sistema exibe uma mensagem de erro.

---

### [RF003] Consulta de Disponibilidade de Livro
**Descrição:** Permite que o usuário consulte se um livro está disponível no acervo.  
**Atores:** Usuário, Sistema, Biblioteca.  
**Prioridade:** **Essencial**

#### Entradas e Pré-condições:
- O usuário deverá informar o título ou o código do livro.

#### Saídas e Pós-condições:
- O sistema exibe o status do livro (Disponível, Emprestado ou Reservado).

#### Fluxo Normal:
1. O usuário informa o título ou o código do livro que deseja consultar.
2. O sistema busca o livro no acervo.
3. O sistema exibe o status do livro e sua localização na biblioteca (se disponível).

#### Fluxo Excepcional 1 (Livro não encontrado):
- Se o livro não for encontrado no acervo, o sistema exibe uma mensagem informando que ele não está cadastrado.

---

### [RF004] Reserva de Livro
**Descrição:** Permite que o usuário reserve um livro que esteja emprestado.  
**Atores:** Usuário, Sistema, Biblioteca.  
**Prioridade:** **Importante**

#### Entradas e Pré-condições:
- O usuário deverá informar o código do livro que deseja reservar.  
- O livro deverá estar em status "Emprestado".

#### Saídas e Pós-condições:
- O sistema registra a reserva e informa ao usuário quando o livro estará disponível.

#### Fluxo Normal:
1. O usuário informa ao sistema o código do livro que deseja reservar.
2. O sistema verifica se o livro está em status "Emprestado".
3. O sistema registra a reserva e informa ao usuário a previsão de disponibilidade.

#### Fluxo Excepcional 1 (Livro disponível):
- Se o livro estiver disponível, o sistema informa que a reserva não é necessária e sugere realizar o empréstimo diretamente.

---

### [RF005] Cadastro de Novo Livro
**Descrição:** Permite que o usuário cadastre um novo livro no sistema, fornecendo informações como título, autor e data de publicação.  
**Atores:** Usuário (Bibliotecário), Sistema.  
**Prioridade:** **Essencial**

#### Entradas e Pré-condições:
- O usuário deverá ter acesso ao sistema de gerenciamento de livros e estar na tela de cadastro de livros.

#### Saídas e Pós-condições:
- O sistema adiciona o livro à base de dados, exibindo uma mensagem de confirmação ou erro, conforme o sucesso ou falha da operação.

#### Fluxo Normal:
1. O usuário acessa a tela de cadastro de novo livro.
2. O sistema exibe os campos para preenchimento do título, autor e data de publicação.
3. O usuário preenche os campos obrigatórios com as informações do livro (título, autor, data de publicação).
4. Após preencher os campos, o usuário clica no botão "Cadastrar Livro".
5. O sistema valida as informações. Caso todos os campos obrigatórios estejam preenchidos corretamente, o sistema cadastra o livro no banco de dados.
6. O sistema exibe uma mensagem de sucesso, informando que o livro foi cadastrado com sucesso.
7. O usuário pode visualizar os detalhes do livro cadastrado na tela de lista de livros ou realizar o cadastro de outro livro.

#### Fluxo Excepcional 1 (Campos obrigatórios não preenchidos):
- Se o usuário tentar cadastrar o livro sem preencher algum campo obrigatório (título, autor ou data de publicação), o sistema exibirá uma mensagem de erro em vermelho abaixo do botão de cadastro:  
  **"Todos os campos são obrigatórios".**

#### Fluxo Excepcional 2 (Formato de data inválido):
- Se a data de publicação for informada em um formato inválido (diferente de dd/mm/aaaa), o sistema exibirá uma mensagem de erro:  
  **"Data inválida. Por favor, insira uma data no formato dd/mm/aaaa".**
