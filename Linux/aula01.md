# Guia Passo a Passo — Prática de Linux no Navegador

**Ambiente recomendado:** [Webminal](https://www.webminal.org)  
*(também funciona em [JDoodle](https://www.jdoodle.com/linux-terminal/) e [TutorialsPoint](https://www.tutorialspoint.com/linux_terminal_online.php))*  

---

## 1️Preparação do Ambiente

1. Acesse **[webminal.org](https://www.webminal.org)** e crie uma conta gratuita (ou faça login).  
2. Clique em **Start Terminal**. Você verá um terminal com um prompt parecido com:

   ```bash
   $
   ```

**Dica:**  
Se preferir, teste em:
- [JDoodle Linux Terminal](https://www.jdoodle.com/linux-terminal/)
- [TutorialsPoint Linux Terminal Online](https://www.tutorialspoint.com/linux_terminal_online.php)

---

## Passos com Comandos, Saída e Explicação

### Passo 1 — Onde estou no sistema?
```bash
pwd
```
**Saída esperada:**
```bash
/home/usuario
```
**Explicação:**  
`pwd` mostra o diretório atual. Normalmente você começa em `/home/<seu-usuário>`.

---

### Passo 2 — O que há nesta pasta?
```bash
ls
```
**Saída:**
```bash
Documents  Downloads  Music  Pictures
```
**Explicação:**  
`ls` lista arquivos e pastas do diretório atual.

---

### Passo 3 — Listagem detalhada (permissões, dono, datas)
```bash
ls -l
```
**Saída:**
```bash
drwxr-xr-x 2 usuario usuario 4096 Oct 17 10:20 Documents
-rw-r--r-- 1 usuario usuario  512 Oct 17 10:15 notas.txt
```
**Explicação:**  
A primeira coluna (`drwxr-xr-x`) indica tipo e permissões:  
- **d** = diretório, **-** = arquivo  
- **r** = leitura, **w** = escrita, **x** = execução.  
Depois vêm dono, grupo, tamanho e data.

---

### Passo 4 — Ver arquivos ocultos
```bash
ls -a
```
**Saída:**
```bash
.  ..  .bashrc  Documents  notas.txt
```
**Explicação:**  
Arquivos que começam com `.` são ocultos.  
`.` é o diretório atual, `..` é o diretório pai.

---

### Passo 5 — Criar e entrar em uma pasta de trabalho
```bash
mkdir aula_linux
cd aula_linux
pwd
```
**Saída:**
```bash
/home/usuario/aula_linux
```
**Explicação:**  
`mkdir` cria a pasta, `cd` entra nela e `pwd` confirma o caminho atual.

---

### Passo 6 — Criar, visualizar e complementar um arquivo
```bash
echo "Meu primeiro arquivo Linux" > texto1.txt
cat texto1.txt
echo "Nova linha" >> texto1.txt
nl texto1.txt
```
**Saída:**
```bash
1  Meu primeiro arquivo Linux
2  Nova linha
```
**Explicação:**  
- `>` cria/sobrescreve um arquivo  
- `>>` adiciona conteúdo no final  
- `nl` exibe com numeração de linhas.

---

### Passo 7 — Copiar, renomear e organizar
```bash
cp texto1.txt copia.txt
mv copia.txt renomeado.txt
mkdir backup
mv renomeado.txt backup/
```
**Explicação:**  
- `cp` copia arquivos  
- `mv` renomeia ou move  
- Verifique com `ls` e `ls backup`.

---

### Passo 8 — Explorar conteúdo
```bash
head -n 1 texto1.txt
tail -n 1 texto1.txt
wc texto1.txt
```
**Saída:**
```bash
1  Meu primeiro arquivo Linux
Nova linha
2 5 32 texto1.txt
```
**Explicação:**  
- `head` mostra as primeiras linhas  
- `tail` mostra as últimas  
- `wc` conta linhas, palavras e caracteres.

---

### Passo 9 — Procurar dentro de arquivos
```bash
grep "linha" texto1.txt
```
**Saída:**
```bash
Nova linha
```
**Explicação:**  
`grep` busca uma palavra ou padrão no arquivo.  
Se não encontrar nada, o comando não gera saída.

---

### Passo 10 — Informações do sistema e usuário
```bash
date
uname -a
whoami
```
**Saída:**
```bash
Fri Oct 17 10:45:13 UTC 2025
Linux webminal 5.x.y ...
usuario
```
**Explicação:**  
- `date` mostra data/hora  
- `uname -a` traz informações do kernel  
- `whoami` mostra o usuário atual.

---

### Passo 11 — Permissões
```bash
ls -l texto1.txt
chmod 600 texto1.txt
ls -l texto1.txt
```
**Saída:**
```bash
-rw-r--r-- 1 usuario usuario ... texto1.txt
-rw------- 1 usuario usuario ... texto1.txt
```
**Explicação:**  
`chmod 600` dá permissão de leitura e escrita apenas para o dono.

---

### Passo 12 — Processos
```bash
sleep 60 &
ps | head -n 5
kill %1   # ou kill <PID>
```
**Saída:**
```bash
[1] 1234
PID TTY   TIME CMD
...
[1]+  Terminated  sleep 60
```
**Explicação:**  
- `&` executa em segundo plano  
- `ps` lista processos ativos  
- `kill` encerra o processo pelo job ou PID.

---

### Passo 13 — Entendendo erros (didático)
```bash
cat inexistente.txt
```
**Saída:**
```bash
cat: inexistente.txt: No such file or directory
```
**Explicação:**  
Mensagem de erro comum. Indica que o arquivo não existe — útil para entender erros e corrigir caminhos.

---

### Passo 14 — Script simples
```bash
printf '#!/bin/bash
echo "Olá, mundo Linux!"
date
pwd
ls
' > meu_script.sh
chmod +x meu_script.sh
./meu_script.sh
```
**Saída:**
```bash
Olá, mundo Linux!
Fri Oct 17 10:50:00 UTC 2025
/home/usuario/aula_linux
texto1.txt  backup  meu_script.sh
```
**Explicação:**  
Cria um script executável com comandos internos e o executa no terminal.

---

### Passo 15 — Bônus de filtros úteis
```bash
echo -e "banana
abacate
caju" | sort
```
**Saída:**
```bash
abacate
banana
caju
```
**Explicação:**  
`sort` ordena as linhas alfabeticamente — útil para processar listas e dados.

---

## 3️Checklist de Entrega

Envie um documento contendo:
- Capturas de tela das saídas principais (`pwd`, `ls -l`, `nl`, `wc`, `grep`, `uname -a`, `ps`, `chmod`, `./meu_script.sh`)
- Arquivos `texto1.txt` e `meu_script.sh`  
- Um pequeno parágrafo explicando o que aprendeu sobre **permissões** e **processos**.

---

## 4️Problemas Comuns & Soluções

**Permissão negada ao executar script:**  
Use `chmod +x meu_script.sh` e tente novamente:  
```bash
./meu_script.sh
```

**Arquivo não encontrado:**  
Verifique com `ls` se o arquivo existe e confirme o caminho com `pwd`.

**Processo não encerra com `kill %1`:**  
Liste processos com `ps`, copie o PID e use:  
```bash
kill <PID>
```
Se ainda não encerrar:
```bash
kill -9 <PID>
```

**Observação:**  
Nos terminais do JDoodle ou TutorialsPoint, os nomes de usuário e pastas podem variar, mas o comportamento dos comandos é o mesmo.

---

© 2025 — Guia prático criado para aulas de **Fundamentos de Sistemas Operacionais**  
Uso educacional.
