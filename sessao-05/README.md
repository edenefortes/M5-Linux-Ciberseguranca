# Relatório de Auditoria de Segurança - Lynis


## 1. Score inical: 65

![hardening-index](/sessao-05/evedencias/hardening-index.png)

## 2. Os avisos encontrados: nenhum

![no-warnings](/sessao-05/evedencias/no%20warnings.png
)

## 3. Medidas corretivas

A auditoria identificou três recomendações principais relacionadas com a gestão do sistema de ficheiros, políticas de palavras-passe e configuração do serviço SSH.

### 1. Separar a partição `/var`

Solução recomendada

Criar uma partição (ou volume lógico) dedicada para `/var` e atualizar o ficheiro `/etc/fstab` para que seja montada automaticamente no arranque.

### 2. Configurar a idade máxima das palavras-passe
    Solução recomendada

Editar o ficheiro:

```bash
sudo nano /etc/login.defs
```

Definir uma política semelhante à seguinte:

```text
PASS_MAX_DAYS   90
PASS_MIN_DAYS   7
PASS_WARN_AGE   14
```

Para utilizadores já existentes:

```bash
sudo chage -M 90 utilizador
```
### 3. Reforçar a configuração do SSH
  Solução recomendada

Editar o ficheiro:

```bash
sudo nano /etc/ssh/sshd_config
```

Adicionar ou alterar:

```text
MaxAuthTries 3
```

Validar a configuração:

```bash
sudo sshd -t
```

Reiniciar o serviço:

```bash
sudo systemctl restart ssh
```  



