**O Domínio: Empréstimo de Livros**
Diferente de um CRUD de "Cadastro de Livros", o processo de empréstimo envolve estado, políticas e validações que tornam o DDD interessante.

1. Entidades e Objetos de Valor
Livro (Entidade): Não é apenas um título. Ele tem um Status (Disponível, Emprestado, Reservado, Em Manutenção).

Empréstimo (Agregado/Entidade): Possui uma data de início, data prevista de devolução e o ID do leitor.

Dinheiro/Multa (Objeto de Valor): Para lidar com taxas de atraso.

ISBN (Objeto de Valor): Com validação própria.

2. A "Lógica de Domínio" (Onde o DDD brilha)
Para fugir do CRUD, você deve implementar estas regras dentro das suas classes de domínio, e não nos serviços de aplicação:

Política de Renovação: Um livro só pode ser renovado se não houver uma reserva ativa de outro leitor.

Limite de Posse: Um leitor não pode pegar um novo livro se tiver mais de 3 livros em mãos ou se possuir multas pendentes acima de R$ 10,00.

Cálculo de Atraso: Uma lógica que calcula a multa baseada em dias úteis vs. feriados (aqui você pode usar um Domain Service).
