# 🧠 TalentAI — Sistema Inteligente de Triagem de Candidatos

Automação completa de recrutamento com Inteligência Artificial, integrada a dashboards analíticos para apoio à decisão no RH.



* 📌 Sobre o Projeto
O TalentAI é um sistema end-to-end de triagem de currículos que utiliza IA generativa para analisar candidatos, gerar scores de compatibilidade e alimentar dashboards em tempo real — sem intervenção humana.
O problema que resolve

AntesDepois
❌ Triagem manual e demorada   ✅ Análise automática em segundos
❌ Critérios subjetivos        ✅ Score padronizado por IA
❌ Sem rastreabilidade         ✅ Histórico completo na planilha
❌ Dashboards desatualizados   ✅ Indicadores em tempo real

🏗️ Arquitetura do Sistema
Recrutador acessa a página (Lovable)
        ↓
Preenche nome da vaga + currículo
        ↓
Webhook recebe os dados (n8n)
        ↓
Busca requisitos da vaga (Google Sheets — aba Vagas)
        ↓
IA analisa e gera score (Google Gemini 2.5)
        ↓
CV arquivado como .txt (Google Drive — pasta TalentAI_CVs)
        ↓
Resultado salvo com link do CV (Google Sheets — aba Candidatos)
        ↓
Dashboard atualizado automaticamente (Power BI)

🛠️ Tecnologias Utilizadas
TecnologiaFunçãoLovableInterface web profissional para envio de currículosn8n CloudOrquestração de toda a automaçãoGoogle Gemini 2.5Análise de currículos e geração de score com IAGoogle SheetsBase de dados de candidatos e requisitos de vagasGoogle DriveArquivo dos currículos originais em .txtPower BIDashboards analíticos para o time de RH

⚙️ Como Funciona
1. 🖥️ Interface de Envio (Lovable)
O recrutador acessa a página do TalentAI, informa o nome da vaga e cola o currículo do candidato. A página envia os dados automaticamente via webhook para o n8n.
2. ⚙️ Automação (n8n)
O n8n orquestra todo o fluxo em sequência:

Recebe os dados pelo webhook
Busca os requisitos da vaga na planilha
Envia para análise da IA
Arquiva o CV no Google Drive
Salva o resultado na planilha

3. 🤖 Análise com IA (Google Gemini 2.5)
O Gemini recebe o currículo completo junto com os requisitos obrigatórios e desejáveis da vaga e retorna uma análise estruturada com:

Score de compatibilidade (0 a 100)
Categoria de aderência
Competências identificadas
Lacunas em relação à vaga
Observação para o recrutador

4. 📊 Base de Dados (Google Sheets)
O projeto utiliza duas abas na planilha:
Aba Vagas — requisitos de cada posição:
Nome da VagaRequisitos ObrigatóriosRequisitos DesejáveisNívelExperiência MínimaAnalista de dadosPython, SQL, Power BI, ExcelMachine Learning, TableauPleno2 anosDesenvolvedor backendPython, Docker, REST API, PostgreSQLKubernetes, RedisPleno3 anosUX designerFigma, User Research, PrototipagemMotion Design, Design SystemJúnior/Pleno1 ano
Aba Candidatos — resultado de cada análise:
CampoDescriçãoIDSequencial automáticoNome do CandidatoExtraído do currículo pela IAVagaNome da vaga analisadaData da AnáliseGerada automaticamenteScore (%)0 a 100CategoriaAltamente / Parcialmente / Não AderenteCompetências IdentificadasSkills encontradas no CVLacunasO que falta para a vagaObservação da IAAnálise em 1-2 frasesAnalista"IA Gemini" (automático)Status Final"Em avaliação" (padrão)Link do CVLink direto para o arquivo no Google Drive
5. 🗄️ Arquivo de CVs (Google Drive)
Cada currículo analisado é salvo automaticamente como arquivo .txt no Google Drive, na pasta TalentAI_CVs. O link direto é salvo na planilha para acesso rápido pelo recrutador.
6. 🎯 Classificação de Candidatos
CategoriaScoreSignificado🟢 Altamente Aderente≥ 70Atende os principais requisitos🟡 Parcialmente Aderente40 a 69Atende parte dos requisitos🔴 Não Aderente< 40Não atende os requisitos mínimos

📊 Dashboard Power BI
Painel único com todas as métricas em uma página com tema TalentAI:
KPIs:

Total de Candidatos
Média de Score
Altamente Aderentes
Não Aderentes

Gráficos:

🥧 Distribuição por Categoria (pizza)
📊 Candidatos por Vaga (barras)
🏆 Ranking de Candidatos (tabela ordenada por score com formatação condicional)
