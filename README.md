Conectando WhatsApp ao n8n via HTTP Request (Uzapi)
Este guia prático detalha como realizar a integração do seu WhatsApp com o n8n utilizando a infraestrutura da Uzapi.
1. Cadastro e Configuração Inicial
Acesse o site oficial da Uzapi e realize seu cadastro para obter acesso à API gratuita de testes.
Após o cadastro, você receberá por e-mail a URL do Painel, suas credenciais de acesso e o seu Token de autenticação.
2. Configurando a Conexão no Painel Uzapi
Ao acessar o painel, você precisará definir os identificadores da sua instância:
Session: Nome de identificação (ex: empresa1). Use apenas letras minúsculas, sem espaços ou acentos.
SessionKey: Chave de segurança (pode ser igual à Session, ex: empresa1).
Token: Código único fornecido pela Uzapi após a ativação.
Ação: Siga as instruções do painel para ler o QR Code e conectar seu dispositivo WhatsApp.
3. Configuração no n8n (Nó HTTP Request)
No seu workflow do n8n, adicione um nó do tipo HTTP Request e preencha com as seguintes informações:
Informações Principais
Method: POST
URL: SUA_URL_DO_ENDPOINT/sendText
Authentication: Generic Credential Type
Generic Auth Type: Header Auth
Headers (Parâmetros de Cabeçalho)
No campo Specify Headers, adicione os seguintes parâmetros:
Name	Value
apitoken	Seu Token fornecido no endpoint
sessionkey	Sua SessionKey definida no painel
Body (Corpo da Requisição)
Body Content Type: JSON
Specify Body: Using JSON
JSON:
json
{ 
  "session": "sua_session_aqui", 
  "number": "5511999999999", 
  "text": {{ JSON.stringify($json.mensagem) }} 
}
Use o código com cuidado.


