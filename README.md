<h1 align='center'>E o Oscar vai para... ?</h1>

<h2>Feito por</h2>
<ul>
  <li><a href="https://github.com/selingindev">@selingindev</a></li>
  <li><a href="https://github.com/LuizHms55">@LuizHms55</a></li>
  <li><a href="https://github.com/APBielzinx">@APBielzinx</a></li>
  <li><a href="https://github.com/Ruuhbcs">@Ruuhbcs</a></li>
  <li><a href="https://github.com/AvgvstaDev">@AvgvstaDev</a></li>
  <li><a href="https://github.com/vitorvhsilva">@vitorvhsilva</a></li>
</ul>

<h3>Atividades para trabalhar com o Oscar</h3>

<p>1 -Quantas vezes Natalie Portman foi indicada ao Oscar?</p>

```
SELECT COUNT(*) FROM oscar_database.indicados_ao_oscar WHERE nome_do_indicado = "Natalie Portman";
```

<p>2 - Quantos Oscars Natalie Portman ganhou?</p>

```
SELECT COUNT(*) FROM oscar_database.indicados_ao_oscar WHERE nome_do_indicado = "Natalie Portman" AND vencedor = 'true';
```

<p>3 - Amy Adams já ganhou algum Oscar?</p>

```
SELECT COUNT(*) FROM oscar_database.indicados_ao_oscar WHERE nome_do_indicado = "Amy Adams" AND vencedor = 'true';
```

<p>4 - A série de filmes Toy Story ganhou um Oscar em quais anos?</p>

```
SELECT * FROM oscar_database.indicados_ao_oscar WHERE nome_do_filme LIKE '%Toy Story%';
```

<p>5 - A partir de que ano que a categoria "Actress" deixa de existir? </p>

```
SELECT MAX(ano_cerimonia) AS ultimo_ano FROM indicados_ao_oscar WHERE categoria = 'Actress';
```

<p>6 - O primeiro Oscar para melhor Atriz foi para quem? Em que ano?</p>

```
SELECT nome_do_indicado, ano_cerimonia FROM indicados_ao_oscar WHERE categoria = 'ACTRESS' AND vencedor = 'true' ORDER BY ano_cerimonia ASC LIMIT 1;
```

<p>7 - Na coluna/campo "Vencedor", altere todos os valores com "Sim" para 1 e todos os valores "Não" para 0.</p>

```
UPDATE indicados_ao_oscar SET vencedor = REPLACE(vencedor, 'true', 1), vencedor = REPLACE(vencedor, 'false', 0);
```

<p>8 - Em qual edição do Oscar "Crash" concorreu ao Oscar?</p>

```
SELECT ano_cerimonia FROM indicados_ao_oscar WHERE nome_do_filme = 'Crash' LIMIT 1;
```

<p>9 - Bom... dê um Oscar para um filme que merece muito, mas não ganhou.</p>

```
INSERT INTO indicados_ao_oscar (ano_filmagem, ano_cerimonia, cerimonia, categoria, nome_do_indicado, nome_do_filme, vencedor)
VALUES (2008, 2009, 81, 'Melhor Filme', 'The Dark Knight', 'The Dark Knight', 1);
```

<p>10 - O filme Central do Brasil aparece no Oscar?</p>

```
SELECT * FROM indicados_ao_oscar WHERE nome_do_filme = 'Central do Brasil';
```

<p>11 - Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser. </p>

```
INSERT INTO indicados_ao_oscar (ano_filmagem, ano_cerimonia, cerimonia, categoria, nome_do_indicado, nome_do_filme, vencedor)
VALUES
  (1982, 1983, 55, 'Melhor Filme', 'Blade Runner', 'Blade Runner', 0),
  (1968, 1969, 41, 'Melhor Filme', '2001: A Space Odyssey', '2001: A Space Odyssey', 0),
  (1975, 1976, 48, 'Melhor Filme', 'Monty Python and the Holy Grail', 'Monty Python and the Holy Grail', 0);
```

<p>14 - Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor? </p>

```
SELECT categoria, nome_do_indicado AS vencedor
FROM indicados_ao_oscar
WHERE ano_cerimonia = 2006 AND categoria IN ('ACTRESS IN A LEADING ROLE', 'DIRECTING') AND vencedor = 'true';
```

