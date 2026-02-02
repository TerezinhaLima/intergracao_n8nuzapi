

# Integração WhatsApp com n8n via Uzapi

Este guia fornece o passo a passo para conectar o WhatsApp ao **n8n** utilizando a API da [Uzapi](https://uzapi.com.br).

## 🚀 Primeiros Passos

1. **Cadastro:** Acesse o site da [Uzapi](https://uzapi.com.br) e realize o cadastro para testar a API gratuita.
2. **Acesso:** Entre na URL fornecida por e-mail utilizando as credenciais enviadas pela plataforma.
3. **Conexão:** No painel, conecte seu WhatsApp lendo o QR Code.

### Dados de Conexão (Exemplos)
*   **Session:** `empresa1` (Minúsculo, sem espaços ou acentos).
*   **SessionKey:** `empresa1` (Pode ser igual à session).
*   **Token:** Código único fornecido no painel da Uzapi.

---

## ⚙️ Configuração no n8n (HTTP Request)

Adicione um nó **HTTP Request** no seu workflow e utilize as seguintes configurações:

### 1. Parâmetros Básicos
- **Method:** `POST`
- **URL:** `URL_FORNECIDA_NO_ENDPOINT/sendText`
- **Authentication:** `Generic Credential Type`
- **Generic Auth Type:** `Header Auth`

### 2. Cabeçalhos (Headers)
Selecione **Send Headers** e adicione em **Specify Headers**:

| Name | Value |
| :--- | :--- |
| `apitoken` | Sua Session fornecida no endpoint |
| `sessionkey` | Sua SessionKey fornecida no endpoint |

### 3. Corpo da Requisição (Body)
- **Body Content Type:** `JSON`
- **Specify Body:** `Using JSON`

**JSON:**
```json
{ 
  "session": "sua_session_aqui", 
  "number": "numero_do_telefone", 
  "text": {{ JSON.stringify($json.mensagem) }} 
}
