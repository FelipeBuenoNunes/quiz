# Scripts de Criptografia do Quiz

Este diretório contém scripts para gerenciar as perguntas criptografadas do quiz médico.

## Arquivos

- `generate_encrypted_data.js` - Gera dados criptografados a partir de perguntas.json
- `update_html.js` - Atualiza automaticamente o index.html com novas perguntas
- `perguntas.json` - Arquivo de perguntas em formato legível
- `questions.dat` - Arquivo de perguntas criptografadas
- `index.html` - Jogo principal com dados embedded

## Como Usar

### 1. Para Gerar Dados Criptografados

```bash
node generate_encrypted_data.js
```

Isso vai:
- Ler `perguntas.json`
- Criptografar as perguntas
- Gerar arquivo `encrypted_data_output.js` com o código JavaScript
- Atualizar `questions.dat`

### 2. Para Atualizar Automaticamente o HTML

```bash
node update_html.js
```

Isso vai:
- Ler `perguntas.json`
- Criptografar as perguntas
- Fazer backup do `index.html` atual
- Atualizar automaticamente o `ENCRYPTED_DATA` no HTML
- Atualizar `questions.dat`

### 3. Para Adicionar/Editar Perguntas

1. Edite o arquivo `perguntas.json` com suas novas perguntas
2. Execute `node update_html.js`
3. Pronto! O jogo já está atualizado

## Formato das Perguntas

```json
{
    "perguntas": [
        {
            "id": 1,
            "question": "Sua pergunta aqui?",
            "options": ["Opção A", "Opção B", "Opção C", "Opção D"],
            "correctIndex": 2,
            "explanation": "Explicação para resposta correta",
            "explanationWrong": "Explicação para resposta errada (opcional)"
        }
    ]
}
```

## Segurança

- As perguntas são criptografadas usando XOR + Base64 + embaralhamento
- A chave de criptografia está definida nos scripts como "MedicalQuizSecure2024"
- Os dados ficam embedded no HTML, evitando problemas de CORS
- O arquivo original `perguntas.json` pode ser mantido em segurança

## Backups

O script `update_html.js` automaticamente:
- Cria backup do `index.html` antes de modificar
- Mantém os 5 backups mais recentes
- Remove backups antigos automaticamente