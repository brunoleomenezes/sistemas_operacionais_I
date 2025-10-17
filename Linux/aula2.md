# Práticas de Linux no Navegador — Aulas 2 a 6
**Disciplina:** Fundamentos de Sistemas Operacionais  
**Ambiente:** [Webminal](https://www.webminal.org) ou [JDoodle Linux Terminal](https://www.jdoodle.com/linux-terminal/)  
**Nível:** Iniciante–Intermediário  
**Pré-requisito:** Ter concluído a Aula 1 – *Explorando o Linux no Navegador*

---

## AULA 2 — Mini-Projeto: Sistema de Organização de Arquivos

**Objetivo:**  
Simular um pequeno sistema de diretórios e praticar criação, movimentação e proteção de arquivos.

### Passos

```bash
mkdir projeto
cd projeto
mkdir docs scripts dados
echo "Relatório inicial" > docs/relatorio.txt
echo "Backup dos dados" > dados/info.txt
cp dados/info.txt docs/
chmod 600 docs/relatorio.txt
ls -R
```

### O que acontece
- `mkdir` cria pastas.
- `echo` cria e escreve em arquivos.
- `cp` copia arquivos.
- `chmod` altera permissões.
- `ls -R` mostra a estrutura completa.

### Desafio
Crie uma pasta chamada `relatorios_2025` e mova o arquivo `relatorio.txt` para dentro dela.  
Em seguida, liste toda a estrutura com `tree` ou `ls -R`.

---

## AULA 3 — Shell Script: Calculadora Simples

**Objetivo:**  
Criar um script interativo que realiza operações básicas.

### Passos

Crie o arquivo:
```bash
nano calculadora.sh
```

Cole o conteúdo abaixo:
```bash
#!/bin/bash
echo "Digite o primeiro número:"
read a
echo "Digite o segundo número:"
read b
echo "Escolha a operação (+, -, *, /):"
read op

case $op in
  +) echo "Resultado: $((a + b))";;
  -) echo "Resultado: $((a - b))";;
  \*) echo "Resultado: $((a * b))";;
  /) echo "Resultado: $((a / b))";;
  *) echo "Operação inválida";;
esac
```

Depois, torne-o executável e rode:
```bash
chmod +x calculadora.sh
./calculadora.sh
```

### O que acontece
- `read` lê entradas do usuário.
- `case` compara a operação e executa o cálculo.
- `$(( ))` realiza operações aritméticas.

### Desafio
Adicione ao script uma verificação para impedir divisão por zero.

---

## AULA 4 — Diagnóstico do Sistema

**Objetivo:**  
Gerar um relatório automatizado com informações do sistema.

### Passos
```bash
echo "=== RELATÓRIO DO SISTEMA ===" > relatorio.txt
date >> relatorio.txt
uname -a >> relatorio.txt
whoami >> relatorio.txt
df -h >> relatorio.txt
ps >> relatorio.txt
cat relatorio.txt
```

### O que acontece
- `>` cria/zera um arquivo.
- `>>` adiciona conteúdo.
- `df -h` mostra o uso do disco.
- `ps` mostra processos em execução.

### Desafio
Inclua no final do relatório o total de linhas usando:
```bash
wc -l relatorio.txt >> relatorio.txt
```

---

## AULA 5 — Jogo de Adivinhação com Shell Script

**Objetivo:**  
Trabalhar lógica de repetição e condições com `while` e `if`.

### Passos
Crie o arquivo:
```bash
nano jogo.sh
```

Cole o conteúdo:
```bash
#!/bin/bash
num=$((RANDOM % 10 + 1))
tentativas=0
while true; do
  echo "Adivinhe o número (1 a 10):"
  read palpite
  tentativas=$((tentativas + 1))
  if [ "$palpite" -eq "$num" ]; then
    echo " Acertou em $tentativas tentativas!"
    break
  else
    echo " Errado, tente de novo."
  fi
done
```

Torne o script executável e rode:
```bash
chmod +x jogo.sh
./jogo.sh
```

### O que acontece
- `RANDOM` gera um número aleatório.
- `while` repete até o acerto.
- `if` compara o palpite.
- `break` encerra o loop.

### Desafio
Permita que o usuário escolha o intervalo máximo (ex: 1–50) e use essa entrada para o cálculo do número aleatório.

---

## AULA 6 — Gerenciando Permissões e Criando Backups

**Objetivo:**  
Consolidar o aprendizado criando um script de backup e testando permissões.

### Parte 1 — Testando permissões
```bash
echo "dados importantes" > confidencial.txt
ls -l confidencial.txt
chmod 600 confidencial.txt
ls -l confidencial.txt
```
**Explicação:**  
Permissão 600 = apenas o dono pode ler e escrever.

---

### Parte 2 — Script de backup automatizado

Crie o arquivo:
```bash
nano backup.sh
```

Cole o conteúdo:
```bash
#!/bin/bash
origem="docs"
destino="backup_$(date +%Y%m%d_%H%M)"
mkdir "$destino"
cp -r "$origem" "$destino/"
echo "Backup concluído em $destino"
```

Execute:
```bash
chmod +x backup.sh
./backup.sh
```

### O que acontece
- `$(date +%Y%m%d_%H%M)` gera um nome com data e hora.
- `mkdir` cria o diretório de destino.
- `cp -r` copia recursivamente todos os arquivos.

### Desafio
Adicione ao script uma linha que compacte o backup:
```bash
tar -czf "$destino.tar.gz" "$destino"
```

---

## Avaliação do Módulo Prático

| Aula | Título | Competências desenvolvidas | Produto final |
|------|---------|-----------------------------|----------------|
| 1 | Comandos básicos e sistema de arquivos | Navegação e manipulação de arquivos | `meu_script.sh`, `texto1.txt` |
| 2 | Organização de arquivos | Estruturação de diretórios e permissões | Pasta `projeto/` |
| 3 | Scripts e lógica de decisão | Estruturas condicionais e leitura de entrada | `calculadora.sh` |
| 4 | Relatórios e automação | Redirecionamento e comandos de sistema | `relatorio.txt` |
| 5 | Controle de fluxo (loop e variáveis) | Estruturas de repetição e operadores | `jogo.sh` |
| 6 | Permissões e backup | Automação e segurança | `backup.sh` e pasta `backup_YYYYMMDD` |

---

## Conclusão

Após concluir as seis aulas, o aluno deve:
- Dominar os comandos básicos do terminal Linux.  
- Entender permissões, processos e variáveis.  
- Criar e executar scripts Shell com segurança.  
- Ser capaz de automatizar tarefas e gerar relatórios.

---

© 2025 — Material didático elaborado para a disciplina **Fundamentos de Sistemas Operacionais**  
