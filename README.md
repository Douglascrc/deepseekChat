# ChatBot WhatsApp

Este projeto é um chatbot que integra o WhatsApp com um modelo de linguagem rodando no LM Studio. Ele utiliza a biblioteca [whatsapp-web.js](https://github.com/pedroslopez/whatsapp-web.js) para gerenciar a conexão com o WhatsApp, e [axios](https://axios-http.com/) para enviar requisições HTTP ao servidor do LM Studio.

## Funcionalidades

- Conexão com o WhatsApp via WhatsApp Web.
- Geração de QR Code para autenticação.
- Processamento de mensagens recebidas.
- Envio do histórico de conversa e mensagem do usuário para LM Studio.
- Resposta automática utilizando o modelo de linguagem.

## Estrutura de arquivos

- **index.js**: Código principal do chatbot, que inicializa o cliente do WhatsApp, lida com as mensagens e integra com o LM Studio.
- **package.json**: Define as dependências do projeto e scripts.
- **.gitignore**: Especifica arquivos e pastas que não devem ser rastreados pelo Git.

## Requisitos

- [Node.js](https://nodejs.org/) (versão recomendada ≥ 14)
- LM Studio instalado e em execução no host (o servidor deve estar acessível na rede, por exemplo, em `http://localhost:1234`)
- Conexão à internet para baixar dependências

## Instalação

1. Clone ou faça o download do repositório.
2. Navegue até a pasta do projeto:
   ```bash
   cd deepseekChat/
   ```
3. Instale as dependências:
   ```bash
   npm install
   ```

## Configuração

- Certifique-se de que o LM Studio está configurado para escutar em um endereço acessível (por exemplo, `0.0.0.0`) e que o firewall permite conexões na porta utilizada (neste exemplo, porta 1234).
- No arquivo `index.js`, verifique a URL de conexão ao LM Studio:
   ```javascript
   const response = await axios.post('http://localhost:3000/v1/chat/completions', { ... });
   ```
   Ajuste se necessário para refletir o endereço IP e porta corretos.

## Uso

1. Execute o projeto:
   ```bash
   node index.js
   ```
2. Um QR Code será gerado no terminal. Escaneie-o com o WhatsApp para autenticar o cliente.
3. Após a autenticação, quando o cliente estiver pronto, o terminal exibirá:
   ```
   Client is ready!
   ```
4. Ao receber mensagens no WhatsApp, o chatbot enviará a mensagem (junto com o histórico) para o LM Studio e responderá com a resposta gerada.

## Logs e Depuração

- Mensagens de log são exibidas no console para facilitar a verificação da comunicação e depuração.
- Em caso de erro, a mensagem de erro será logada pelo console.

## Considerações Finais

- Este projeto foi desenvolvido para demonstrar a integração entre WhatsApp e um modelo de linguagem via LM Studio.
- Certifique-se de ter configurado corretamente as regras de firewall e rede para permitir a comunicação entre os sistemas (por exemplo, entre o WSL e o host Windows ou entre diferentes interfaces de rede).

## Licença

Este projeto está licenciado sob a licença MIT.