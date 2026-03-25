# CodeSpace Quick Guide
---
Com certeza! Aqui está o conteúdo completo e sequencial em texto puro. Basta copiar o bloco abaixo e colar no seu arquivo `.md` (como o Notepad++, VS Code ou até no Samsung Notes).

---

# 📘 GUIA COMPLETO: RCLONE, POWERSHELL E GITHUB CODESPACES
**Configuração, Otimização e Produtividade (Windows & Android S6 Lite)**

---

## 1. INSTALAÇÃO E CONFIGURAÇÃO (WINDOWS)

### 1.1. Instalação via PowerShell (WinGet)
O WinGet é a forma mais limpa de instalar ferramentas no Windows 10/11.
1. Abra o PowerShell como **Administrador**.
2. Execute o comando:
   `winget install Rclone.Rclone`
3. Reinicie o PowerShell para atualizar as variáveis de ambiente:
   `Start-Process powershell; exit`

### 1.2. Comandos Essenciais do Rclone
* `rclone config` - Inicia a configuração de uma nova nuvem (OneDrive, GDrive, etc).
* `rclone version` - Verifica se a instalação foi bem-sucedida.
* `rclone config file` - Mostra o caminho onde o arquivo de configuração está salvo.

---

## 2. INTEGRAÇÃO NO ANDROID (TERMUX & ACODE)

### 2.1. Compartilhando Configurações
Para não configurar o OneDrive duas vezes, aponte o Termux para o arquivo do Acode.
1. No Acode (Terminal), descubra o local: `rclone config file`.
2. No Termux, crie um alias no arquivo `.bashrc`:
   `nano ~/.bashrc`
3. Adicione a linha:
   `alias rclone='rclone --config /caminho/do/arquivo/acode/rclone.conf'`
4. Salve (`Ctrl+O`, `Enter`) e saia (`Ctrl+X`).

### 2.2. Colar Comandos no Termux
No terminal do Android, o `Ctrl+V` não funciona como no Windows.
* **Procedimento:** Toque e segure em qualquer lugar da tela preta e selecione **PASTE** no menu flutuante.

---

## 3. ESTRATÉGIA GITHUB CODESPACES (ECONOMIA DE HORAS)

### 3.1. Entendendo o Consumo de Horas (Cores)
O plano gratuito oferece **120 core-hours** mensais.
* **Máquina 2-Cores (Mínima):** 60 Horas reais de uso.
* **Máquina 4-Cores:** 30 Horas reais de uso.

### 3.2. Configuração de Timeout (Crítico)
Para evitar gasto de horas com a aba fechada:
1. Vá em **GitHub > Settings > Codespaces**.
2. No item **Default idle timeout**, altere para **5 minutos**.
3. No VS Code, use o comando: `Ctrl+Shift+P` > `Codespaces: Stop Current Codespace` para desligar na hora.

### 3.3. Monitoramento de Créditos
Verifique quanto resta de suas 60 horas em:
`GitHub > Settings > Billing and plans > Plans and usage > Codespaces (Compute)`

---

## 4. GESTÃO DE ARMAZENAMENTO (OS 15GB)

Para nunca exceder o limite de 15GB de disco:
1. **Início:** Abra o Codespace e faça o `git pull` para trazer o código.
2. **Fim do Trabalho:** Faça o `git push` para salvar tudo no GitHub.
3. **Limpeza:** Se não for usar o projeto nos próximos dias, vá em `github.com/codespaces` e **Delete** o ambiente. 
   * Isso apaga os arquivos temporários e zera o uso dos 15GB, mantendo seu código seguro no repositório principal.

---

## 5. EXPERIÊNCIA NO TABLET SAMSUNG S6 LITE

### 5.1. Instalando como PWA (App em Tela Cheia)
1. Abra o Codespace no **Chrome**.
2. Clique nos **três pontinhos (⋮)** no topo do navegador.
3. Selecione **Instalar aplicativo** (ou Adicionar à tela inicial).
4. O ícone aparecerá no seu menu de apps. Abra por ele para ocultar as barras do navegador.

### 5.2. Otimização de Tela
* **Modo Desktop:** Sempre ative "Para Computador" no Chrome.
* **S-Pen:** Excelente para selecionar códigos e clicar em ícones pequenos sem precisar de mouse.
* **Teclado:** Se usar teclado físico, lembre-se que `Ctrl+W` fecha a aba. Prefira o comando de **Stop** interno do VS Code.

---
*Documento gerado em: 20 de Março de 2026.*

---

**Ficou fácil de copiar e colar? Gostaria de adicionar algum tópico específico sobre Git ou Rclone antes de finalizarmos?**