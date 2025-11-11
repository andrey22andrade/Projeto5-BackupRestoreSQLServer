# Projeto 5 - Backup e Restore no SQL Server

Este repositório faz parte do meu portfólio como **DBA Júnior**, demonstrando conhecimentos sobre **backup, restore e estratégias de recuperação de dados** no **SQL Server**.  
O projeto apresenta os principais tipos de backup, fases do restore, opções de configuração e práticas de segurança e desempenho.

---

## 🎯 Objetivo

Demonstrar na prática as rotinas essenciais de **Backup e Restore**, abordando:

- **Backup Full, Diferencial e Log de Transações**
- **Planejamento RPO e RTO**
- **Execução de Restore com segurança**
- **Tail-Log Backup e recuperação após falha**
- **Verificação e validação de integridade**
- **Boas práticas de backup em produção**
- **Comandos T-SQL e Interface Gráfica (SSMS)**

---

## 🧠 Conceitos Aplicados

### ✅ Tipos de Backup
- **Full** → Cópia completa do banco de dados (MDF + NDF + Log ativo).  
- **Diferencial** → Copia apenas os dados alterados desde o último Full.  
- **Log** → Copia o log (LDF) e trunca o espaço inativo.  
- **Log NO_TRUNCATE** → Usado quando o banco está danificado, mas o log íntegro.  

### ✅ Planejamento de Backup
- **RPO (Recovery Point Objective):** define quanto de dado é aceitável perder.  
- **RTO (Recovery Time Objective):** tempo aceitável para restaurar o ambiente.  
- Políticas de retenção, testes periódicos de restore e alertas de falha.  

### ✅ Fases do Restore
1. **Cópia:** grava os dados do backup nos arquivos MDF e LDF.  
2. **Recovery:** executa o Redo e Undo das transações.  
   - `WITH RECOVERY` → finaliza o processo  
   - `WITH NORECOVERY` → aguarda novos restores  
   - `WITH STANDBY` → modo somente leitura  

### ✅ Tail-Log Backup
- Salva as transações que ocorreram após o último backup antes da falha.  
- Permite recuperar alterações entre a falha e o último backup completo.  

### ✅ Estratégias de Backup e Restore
- **Full:** indicado para ambientes de teste e DW.  
- **Full + Log:** rotina básica de produção.  
- **Full + Dif + Log:** ideal para bancos médios / grandes.  
- **File / Filegroup:** usado em bases com múltiplos arquivos.  

### ✅ Opções Avançadas
- `FORMAT`, `INIT`, `NOINIT`, `COMPRESSION`, `CHECKSUM`, `MIRROR TO`  
- `COPY_ONLY` → gera backup independente sem afetar a cadeia de backups.  
- Histórico de backups armazenado em `msdb`.  

---

## 📂 Estrutura do Projeto

📁 Projeto5-BackupRestoreSQLServer  
┣ 📂 scripts/  
┃ ┗ 📜 01-Executando_Backup_e_Restore.sql  
┣ 📂 imagens/  
┣ 📜 README.md  

---

## ▶️ Como Executar

1. Abrir o **SQL Server Management Studio (SSMS)**  
2. Conectar à instância do SQL Server  
3. Executar o script principal:  
   - [01-Executando_Backup_e_Restore.sql](scripts/01-Executando_Backup_e_Restore.sql)  
4. Validar a execução observando os resultados no painel de Mensagens ou Object Explorer.  

---

## 📊 Resultados Esperados

- ✅ Backups Full, Dif e Log gerados com sucesso  
- ✅ Restore realizado sem erro com verificação de integridade  
- ✅ Tail-Log Backup efetivo em simulação de falha  
- ✅ Compressão e validação de backups com CHECKSUM  
- ✅ Estratégias de recuperação documentadas e testadas  

---

## 📌 Observações

Projeto desenvolvido durante o **Módulo 5 – Backup e Restore** do meu curso de formação em Banco de Dados com o Prof. **Landry**.

---

✉️ **Autor:** [Andrey Andrade](https://github.com/andrey22andrade)
