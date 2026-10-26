# Sistema de Prospecção — versão inicial

Aplicação Streamlit para importar planilhas fictícias, identificar duplicados, organizar uma fila manual e exportar relatórios.

## Importante

Esta é uma versão de demonstração. Os registros ficam em `st.session_state`, portanto **não são persistentes** e podem desaparecer quando a sessão reiniciar. Use somente dados fictícios. Não coloque CPFs reais, dados financeiros, credenciais ou listas de servidores nesta versão.

Não há integração com LEMIT, Santander ou qualquer sistema externo.

## Rodar no Windows

1. Instale Python 3.11 ou mais recente e marque "Add Python to PATH" no instalador.
2. Extraia o ZIP para uma pasta.
3. Abra a pasta no VS Code ou abra o terminal dentro dela.
4. Execute:

```powershell
py -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
```

5. Configure a senha da aplicação no terminal antes de iniciar:

```powershell
$env:APP_PASSWORD="coloque-uma-senha-forte-aqui"
$env:DEMO_MODE="true"
python -m streamlit run app.py
```

O navegador deverá abrir. Se não abrir, acesse `http://localhost:8501`.

Não use a senha de exemplo acima; escolha uma senha única e forte.

## Publicar online com GitHub + Streamlit Community Cloud

1. Crie uma conta no GitHub e um repositório **privado** para o projeto.
2. Envie os arquivos deste pacote ao repositório (`app.py`, `requirements.txt`, `README.md`, `dados_ficticios.csv`, `.gitignore` e `.streamlit/secrets.toml.example`). O `app.py` precisa ficar na **raiz** do repositório. Nunca envie senhas, tokens, arquivos `.env` ou `secrets.toml`.
3. Crie/acesse sua conta no Streamlit Community Cloud e autorize o acesso ao repositório.
4. Crie uma aplicação escolhendo o repositório e `app.py`.
5. Nas configurações de Secrets da aplicação, adicione:

```toml
APP_PASSWORD = "substitua-por-uma-senha-forte-e-unica"
DEMO_MODE = "true"
```

6. Em **Advanced settings**, escolha Python 3.11 ou 3.12.
7. Publique e teste apenas com `dados_ficticios.csv`.

### Atenção à segurança online

A senha única deste protótipo é uma barreira simples, não um sistema completo de autenticação empresarial. O endereço da aplicação pode ser acessível pela internet. Antes de usar dados reais, é necessário avaliar a hospedagem, o acesso restrito, os termos do serviço, backups, logs, retenção e a LGPD. Não use dados reais nesta versão de demonstração.

## Próxima etapa antes de produção

Implementar banco de dados persistente e autenticação robusta, permissões e trilha de auditoria, política de retenção, backups e teste de restauração. A conexão com sistemas externos só deve ser considerada após autorização formal e uso dos métodos permitidos pelos fornecedores.

## Funcionalidades

- Importação de CSV e XLSX.
- Identificação preliminar de duplicados por nome + órgão + município.
- Fila manual com status separados para LEMIT e Santander.
- Pesquisa e filtro de registros.
- Exportação para Excel e CSV.
- Dados de teste fictícios.
