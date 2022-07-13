# Webhook-consulta-pratica
Documentação de integração com o Bonsae
Essa documentação serve para a consulta de práticas refentes a uma turma no modelo antigo ou para o novo modelo acadêmico. (Caso sua instituição nunca tenha realizado qualquer integração com a Bonsae antes, siga os passos apenas do novo modelo do acadêmico.)<br>

A consulta das práticas pode ser feita a qualquer momento do dia ou do período letivo previamente cadastrado*, basta fazer uma requisição do tipo POST.

*No novo modelo do acadêmico da Bonsae, pense na estrutura de cadastro das Turmas em 4 “caixas”: Período Letivo > Turmas > Disciplinas > Práticas. O Período Letivo detém as datas de início e fim das turmas que, consequentemente influenciam as datas de início e fim das disciplinas e práticas vinculadas a elas. Esclarecendo a orientação acima, é possível puxar as informações das práticas a qualquer momento ou configurar para que os dados sejam puxados ao final de um período letivo.

Variáveis
variável	tipo	Descrição
token	string	Token gerado pela nossa equipe para sua instituição. Basta requisitar o token pelo e-mail [email protected] ou entrar em contato diretamente pelo contato (61) 99232-9091.
discine_code	string	Codigo dá turma/disciplina consultada
Retorno da requisição
url:https://instancia.bonsae.com.br/api/webhook/practice

*“instancia” na URL acima se refere ao nome da IES, campus ou unidade que a insituição irá implantar a Bonsae. De acordo com a quantidade de campus, a URL pode ter um ou dois formatos. Exemplo de formatos.: "unit.bonsae.com.br" ou "unit.aracaju.bonsae.com.br". Confirme com a coordenação do curso ou com a própria equipe Bonsae qual dos dois formatos será utilizado para o seu caso específico.

{
    <span class="hljs-string">"name"</span>: <span class="hljs-string">"xxt"</span>,
    <span class="hljs-string">"code"</span>: <span class="hljs-string">"dfsaf"</span>,
    <span class="hljs-string">"practices"</span>: [
        {
            <span class="hljs-string">"students"</span>: [
                {
                    <span class="hljs-string">"name"</span>: <span class="hljs-string">"aluno"</span>,
                    <span class="hljs-string">"registration_number"</span>: null,
                    <span class="hljs-string">"email"</span>: <span class="hljs-string">"<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="72131e071c1d32101d1c0113175c111d1f">[email&#xA0;protected]</a>"</span>,
                    <span class="hljs-string">"cpf"</span>: null,
                    <span class="hljs-string">"workload_real"</span>: <span class="hljs-string">"00:00:00"</span>,
                    <span class="hljs-string">"workload_simulated"</span>: null,
                    <span class="hljs-string">"grade"</span>: null,
                    <span class="hljs-string">"presence"</span>: <span class="hljs-number">0</span>,
                    <span class="hljs-string">"observations"</span>: null
                }
            ],
            <span class="hljs-string">"is_simulated"</span>: <span class="hljs-number">1</span>,
            <span class="hljs-string">"name"</span>: <span class="hljs-string">"fsagfasgasdgfa"</span>,
            <span class="hljs-string">"start_date"</span>: <span class="hljs-string">"2022-06-28"</span>,
            <span class="hljs-string">"end_date"</span>: <span class="hljs-string">"2022-07-01"</span>,
            <span class="hljs-string">"grade"</span>: <span class="hljs-number">10</span>,
            <span class="hljs-string">"practice_type_id"</span>: <span class="hljs-number">1</span>,
            <span class="hljs-string">"type"</span>: <span class="hljs-string">"Aps"</span>
        },
        {
            <span class="hljs-string">"students"</span>: [
                {
                    <span class="hljs-string">"name"</span>: <span class="hljs-string">"aluno"</span>,
                    <span class="hljs-string">"registration_number"</span>: null,
                    <span class="hljs-string">"email"</span>: <span class="hljs-string">"<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="aecfc2dbc0c1eeccc1c0ddcfcb80cdc1c3">[email&#xA0;protected]</a>"</span>,
                    <span class="hljs-string">"cpf"</span>: null,
                    <span class="hljs-string">"workload_real"</span>: <span class="hljs-string">"00:00:00"</span>,
                    <span class="hljs-string">"workload_simulated"</span>: null,
                    <span class="hljs-string">"grade"</span>: null,
                    <span class="hljs-string">"presence"</span>: <span class="hljs-number">0</span>,
                    <span class="hljs-string">"observations"</span>: null
                }
            ],
            <span class="hljs-string">"is_simulated"</span>: <span class="hljs-number">1</span>,
            <span class="hljs-string">"name"</span>: <span class="hljs-string">"fsagfasgasdgfa"</span>,
            <span class="hljs-string">"start_date"</span>: <span class="hljs-string">"2022-06-28"</span>,
            <span class="hljs-string">"end_date"</span>: <span class="hljs-string">"2022-07-01"</span>,
            <span class="hljs-string">"grade"</span>: <span class="hljs-number">10</span>,
            <span class="hljs-string">"practice_type_id"</span>: <span class="hljs-number">1</span>,
            <span class="hljs-string">"type"</span>: <span class="hljs-string">"Aps"</span>
        },
    ]
}
variável	tipo	Descrição
students	array	Array de alunos
students[name]	string	Nome do aluno
students[registration_number]	string	Matrícula do aluno
students[email]	string	Email do aluno
students[cpf]	string	CPF do aluno
students[workload_real]	string	Carga hóraria acumulada de práticas reais
students[workload_simulated]	string	Carga hóraria acumulada de práticas simuladas
students[grade]	string	Nota do aluno nas práticas (Prática Acadêmica, APS, Evento Acadêmico ou Projeto)
students[presence]	string	Presença do aluno
students[observations]	string	Feedback que o professor deu sobre a prática do aluno
is_simulated	Boolean	Tipo da prática (simulada ou real)
name	String	Nome da prática
start_date	Date	Data inicial da prática
end_date	Date	Data final da prática
grade	float	Pontuação máxima da prática
type	array	Tipo da prática (Aps, Prática Acadêmica, Evento Acadêmico ou Projeto)
