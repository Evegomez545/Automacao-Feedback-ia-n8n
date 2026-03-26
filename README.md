# 🤖 Agente de IA para Monitoramento de Qualidade (n8n + Gemini)
Este repositório contém o workflow de uma automação inteligente desenvolvida no n8n. O sistema atua como um "Supervisor de Qualidade Virtual", analisando feedbacks de consultoria e agindo proativamente quando a satisfação do cliente fica abaixo da meta.

🚀 Como Funciona o Fluxo
Gatilho Agendado: O fluxo roda automaticamente todos os dias às 09h.

Coleta de Dados: Conecta-se à API do Google Sheets para ler as avaliações de consultoria do dia anterior.

Análise de Dados: * Calcula a média das notas de satisfação.

Um nó If verifica se a média foi inferior a 7.

Processamento com IA (LLM): * Caso a nota seja baixa, o sistema concatena todos os comentários de melhoria.

Um Agente de IA (Google Gemini) analisa os textos, agrupa por temas (ex: atrasos, domínio técnico) e gera um feedback construtivo em formato HTML.

Entrega: * O sistema converte a base de dados em um arquivo .xlsx.

Envia um e-mail via Gmail para o supervisor com o resumo da IA e a planilha completa em anexo.

🛠️ Tecnologias Utilizadas
n8n: Orquestrador do workflow.

Google Gemini (LangChain): Modelo de linguagem para análise de sentimento e síntese de feedbacks.

Google Sheets API: Fonte de dados das consultorias.

Gmail API: Distribuição dos relatórios de qualidade.

Lógica de Dados: Nós de Summarize, Merge e Binary Conversion.

📊 Diferenciais Técnicos
Engenharia de Prompt: O agente de IA possui um System Message detalhado para garantir um tom de mentoria e saídas em HTML limpo.

Gestão de Memória: Uso de Window Buffer Memory para o agente manter o contexto da análise.

Eficiência de Dados: O fluxo só consome tokens de IA e envia alertas se a condição crítica (Nota < 7) for atingida.
