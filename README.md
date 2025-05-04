# SkinShop
![image](https://github.com/user-attachments/assets/432d8bcd-f804-46c5-9d1a-3be30090c433)

**SkinShop** 
<br>É um plugin para servidores Minecraft (versão 1.21.4 Java e Bedrock com Geyser/Floodgate) que permite aos jogadores comprar, aplicar, visualizar e gerenciar skins personalizadas usando o plugin SkinsRestorer.

## Recursos

* Interface para listas de skins com suporte ao CommandPanels
* Totalmente compatível com jogadores Bedrock via Floodgate
* Sistema de inventário com paginação para exibir skins adquiridas
* Integração completa com SkinsRestorer (armazenamento e aplicação de skins)
* Suporte a banco de dados SQLite e MySQL para persistência das skins
* Comandos administrativos para dar/remover skins

## Comandos de Usuários

```bash
/myskin list        # Visualiza e aplica skins pessoais
/myskin <nickname>  # Aplica uma skin de sua lista pessoal
/myskin help        # mostra todos os comandos de usúario

```

## Comandos para Administradores

```bash
/skinshop help                          # Visualiza os comandos
/skinshop reload                        # Recarrega as configurações
/skinshop <nickname> add <skinName>     # Adiciona uma skin ao jogador
/skinshop <nickname> remove <skinName>  # Remove uma skin do jogador
/skinshop <nickname> list               # Lista todas as skins do jogador
/skinshop version                       # Mostra a versão do plugin
```

## Permissões

```yaml
skinshop.admin: Acesso a comandos administrativos (/skinshop)
skinshop.use: Permite usar o comando /myskin
```
Por padrão o skinshop.use já vem habilitado para todos, para remover o acesso é necessario deixar 
o `skinshop.use false`

## Requisitos

* Java 17+
* Minecraft 1.21.4+
* SkinsRestorer 15.6.2+ instalado e configurado
* CommandPanels 3.22.2+ instalado para renderizar GUIs
* Floodgate Build #116+ (para suporte Bedrock, opcional mas recomendado)

## Como usar

1. **Instale** SkinsRestorer e CommandPanels
2. **Adicione** o plugin SkinShop na pasta `plugins/`
3. **Crie** suas skins no formato `.customskin` https://skinsrestorer.net/generator
4. **Dê skins aos jogadores** usando a API ou comando
5. Os jogadores podem aplicar suas skins pelo comando ou pelo menu /myskin list

## Estrutura de arquivos

```
plugins/
  SkinShop/
    skins/
      steve.customskin
      alex.customskin
    config.yml
    skins.db (ou conexão MySQL)
  CommandPanels/
    panels/
      skinshop_<nickname>_p1.yml
```
## Arquivo de configuração CONFIG.YML
```
# -----------------------------------------------------
#   _____ _    _         _____ _                 
#  /  ___| |  (_)       /  ___| |                
#  \ `--.| | ___ _ __  \ `--.| |__   ___  _ __  
#   `--. \ |/ / | '_ \  `--. \ '_ \ / _ \| '_ \ 
#  /\__/ /   <| | | | | /\__/ / | | | (_) | |_) |
#  \____/|_|\_\_|_| |_| \____/|_| |_|\___/| .__/ 
#                                        | |    
#                                        |_|    
# -----------------------------------------------------

# Tipo de armazenamento disponível:
# SQLITE - Recomendado para servidores pequenos ou uso local
# MYSQL - Recomendado para servidores maiores com múltiplos plugins compartilhando dados

storage-type: SQLITE  # ou MYSQL

# Configuração do banco de dados, usada quando o tipo for MYSQL
database-configuration:
  # Prefixo aplicado em todas as tabelas
  table-prefix: "skinshop_"

  # Dados de conexão (necessários apenas se storage-type for MYSQL)
  host: 127.0.0.1
  port: 3306
  user: root
  password: 'senha-aqui'
  database: skinshop

  # Ativa ou desativa logs SQL detalhados
  debug: false
```

## Desenvolvedor

Plugin criado por Valdeci Danilo

> Contribuições, feedbacks e ideias são bem-vindos!
