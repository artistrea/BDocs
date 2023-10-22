# Diagrama do Modelo Relacional
![Alt text](DiagramaRelacional.png)

[link para o dbDiagram](https://dbdiagram.io/d/Trab-BD-63370a017b3d2034fff95595)

- Para diferenciar se um Item é um livro ou MaterialDidatico se utiliza do atributo chave type, que é um Enum que pode ser livro ou materialDidatico.
- O status da Tabela Emprestimos é um Enum que pode ser: emAndamento ou concluido.
- A função da Tabela Usuario é um Enum que pode ser: administrador, chefe ou estudante.