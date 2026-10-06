# Respostas · Avaliação Prática de Docker · Cooperativa AgroVale (Turma A)

Nome: Thiago Alberto Caetano dos Anjos
Matrícula: 26128575
Usuário do GitHub: thiagocaetanoanjod-hue
Usuário do Docker Hub: reozin

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile ou compose vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?
Nome: teste-portal
Tamanho: 21MB

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para conferir que o `index.html` está lá dentro.
# R1.2  O conteúdo de portal/html/ copiado para a pasta de onde o Nginx serve os arquivos. 
COPY html/ /usr/share/nginx/html

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.
Nome: reozin/agrovale-portal:1.0-26128575
Link: https://hub.docker.com/repository/docker/reozin/agrovale-portal/general

4. Por que o `docker login` foi feito com um token de acesso e não com a senha da conta?

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | `WORKDIR` | O Workdir não procurava um arquivo html para servir. | Ele abriu a página padrão do nginx. | Coloquei `/html` no final da linha. |
| 2 | Nenhuma | Ele não tinha a linha de COPY. | Ele não pegou o arquivo certo. | Adicionei a linha `COPY site/ .` |
| 3 | Nenhuma | Sem EXPOSE. | Abria na porta errada. | Coloquei a linha `EXPOSE 80` no final para quando não abrir a porta certa ele abrir o arquivo de erro. |

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?
Quem é a porta, no primeiro caso a porta do conteiner é 7075, já no segundo é 80

## Parte 4 · docker-compose.yml

7. No serviço `blog`, por que `WORDPRESS_DB_HOST` recebe `db` e não `localhost`? 
Pois o WORDPRESS é um banco de dados e foi feito para comportar esse tipo de arquivo, o localhost não

8. Por que o serviço `db` não publica a porta 3306? Se precisar consultar o banco, como faz sem publicar a porta? Mostre o comando.
Por segurança, já que fora da porta 3306, o banco de dados fica isolado do muido externo, ou seja, só o blog pode interagir com ele
docker compose exec db mariadb -u root -p

## Parte 5 · Persistência

9. Quais comandos você usou para derrubar e subir a stack? Qual comando teria apagado o post que você criou,
   e por quê?

10. Código de conclusão impresso pelo verificador:

```
(cole aqui)
```
