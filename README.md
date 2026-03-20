Projeto 2 - Criando um Algoritmo de Recomendação de Músicas Com Base Em Grafos.

Fiz um grafo utilizando .cypher que simula um algoritimo de recomendação de músicas,
tentei faer o codigo de forma separada, utilizei o arrows.app para me basear e com 
ele pude ver que seria melhor criar o codigo de forma separada criando os Usuários,
Artístas, Musicas, depois os Relacionamentos.

Obs: O script foi escriito por um iniciante *PODE CONTER FALHAS*

Código completo:

// ======================================
// PROJETO 2 - SISTEMA DE RECOMENDAÇÃO DE MÚSICAS
// ======================================

// ---------------------------
// 1. Limpar banco (opcional)
// ---------------------------
MATCH (n)
DETACH DELETE n;

// ---------------------------
// 2. Criar usuários
// ---------------------------
CREATE
(u1:User {id: 1, nome: 'Gabriel'}),
(u2:User {id: 2, nome: 'Ana'}),
(u3:User {id: 3, nome: 'Carlos'}),
(u4:User {id: 4, nome: 'Julia'});

// ---------------------------
// 3. Criar artistas
// ---------------------------
CREATE
(a1:Artist {id: 1, nome: 'The Weeknd'}),
(a2:Artist {id: 2, nome: 'Imagine Dragons'}),
(a3:Artist {id: 3, nome: 'Ariana Grande'}),
(a4:Artist {id: 4, nome: 'Bruno Mars'});

// ---------------------------
// 4. Criar gêneros
// ---------------------------
CREATE
(g1:Genre {id: 1, nome: 'Pop'}),
(g2:Genre {id: 2, nome: 'Rock'}),
(g3:Genre {id: 3, nome: 'R&B'});

// ---------------------------
// 5. Criar músicas
// ---------------------------
CREATE
(m1:Music {id: 1, titulo: 'Blinding Lights'}),
(m2:Music {id: 2, titulo: 'Believer'}),
(m3:Music {id: 3, titulo: '7 Rings'}),
(m4:Music {id: 4, titulo: 'Locked Out of Heaven'}),
(m5:Music {id: 5, titulo: 'Save Your Tears'}),
(m6:Music {id: 6, titulo: 'Thunder'}),
(m7:Music {id: 7, titulo: 'Into You'}),
(m8:Music {id: 8, titulo: 'Grenade'});

// ---------------------------
// 6. Relacionar músicas com artistas
// ---------------------------
CREATE
(m1)-[:CANTA]->(a1),
(m2)-[:CANTA]->(a2),
(m3)-[:CANTA]->(a3),
(m4)-[:CANTA]->(a4),
(m5)-[:CANTA]->(a1),
(m6)-[:CANTA]->(a2),
(m7)-[:CANTA]->(a3),
(m8)-[:CANTA]->(a4);

// ---------------------------
// 7. Relacionar músicas com gêneros
// ---------------------------
CREATE
(m1)-[:PERTENCE_A]->(g3),
(m2)-[:PERTENCE_A]->(g2),
(m3)-[:PERTENCE_A]->(g1),
(m4)-[:PERTENCE_A]->(g3),
(m5)-[:PERTENCE_A]->(g1),
(m6)-[:PERTENCE_A]->(g2),
(m7)-[:PERTENCE_A]->(g1),
(m8)-[:PERTENCE_A]->(g3);

// ---------------------------
// 8. Criar interações dos usuários
// ---------------------------

// Gabriel
CREATE
(u1)-[:ESCUTOU {vezes: 15}]->(m1),
(u1)-[:CURTIU]->(m1),
(u1)-[:ESCUTOU {vezes: 10}]->(m5),
(u1)-[:CURTIU]->(m5),
(u1)-[:SEGUE]->(a1);

// Ana
CREATE
(u2)-[:ESCUTOU {vezes: 20}]->(m1),
(u2)-[:CURTIU]->(m1),
(u2)-[:ESCUTOU {vezes: 12}]->(m4),
(u2)-[:CURTIU]->(m4),
(u2)-[:SEGUE]->(a4);

// Carlos
CREATE
(u3)-[:ESCUTOU {vezes: 18}]->(m2),
(u3)-[:CURTIU]->(m2),
(u3)-[:ESCUTOU {vezes: 11}]->(m6),
(u3)-[:CURTIU]->(m6),
(u3)-[:SEGUE]->(a2);

// Julia
CREATE
(u4)-[:ESCUTOU {vezes: 14}]->(m3),
(u4)-[:CURTIU]->(m3),
(u4)-[:ESCUTOU {vezes: 9}]->(m7),
(u4)-[:CURTIU]->(m7),
(u4)-[:SEGUE]->(a3);

// ---------------------------
// 9. Mais algumas conexões para enriquecer recomendações
// ---------------------------
CREATE
(u2)-[:ESCUTOU {vezes: 8}]->(m5),
(u2)-[:CURTIU]->(m5),
(u4)-[:ESCUTOU {vezes: 7}]->(m5),
(u1)-[:ESCUTOU {vezes: 5}]->(m4),
(u3)-[:ESCUTOU {vezes: 4}]->(m8);


OBS: Utilizei uma 'IA LLM' para organizar o script de forma que ela colocou comentários dentro do script.
