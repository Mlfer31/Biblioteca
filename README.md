# Biblioteca
Criei um banco de dados de uma biblioteca utilizando PostgreSQl

CREATE DATABASE BIBLIOTECA;

CREATE TABLE autores (
    id_autor SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    nacionalidade VARCHAR(50)
);

CREATE TABLE livros (
    id_livro SERIAL PRIMARY KEY,
    titulo VARCHAR(150) NOT NULL,
    ano_publicacao INT,
    id_autor INT REFERENCES autores(id_autor)
);

CREATE TABLE usuarios (
    id_usuario SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE
);

CREATE TABLE emprestimos (
    id_emprestimo SERIAL PRIMARY KEY,
    id_usuario INT REFERENCES usuarios(id_usuario),
    id_livro INT REFERENCES livros(id_livro),
    data_emprestimo DATE NOT NULL,
    data_devolucao DATE
);

INSERT INTO autores (nome, nacionalidade) VALUES
('Machado de Assis', 'Brasileiro'),
('J. K. Rowling', 'Britânica'),
('George Orwell', 'Britânico');


INSERT INTO livros (titulo, ano_publicacao, id_autor) VALUES
('Dom Casmurro', 1899, 1),
('Harry Potter e a Pedra Filosofal', 1997, 2),
('1984', 1949, 3);


INSERT INTO usuarios (nome, email) VALUES
('Ana Souza', 'ana@email.com'),
('Carlos Lima', 'carlos@email.com');


INSERT INTO emprestimos (id_usuario, id_livro, data_emprestimo, data_devolucao) VALUES
(1, 1, '2025-09-01', '2025-09-15'),
(2, 2, '2025-09-05', NULL);

