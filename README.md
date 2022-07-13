# Webhook-consulta-pratica
# Documentação de integração com o Bonsae
Essa documentação serve para a consulta de práticas refentes a uma turma no modelo antigo ou para o novo modelo acadêmico. (Caso sua instituição nunca tenha realizado qualquer integração com a Bonsae antes, siga os passos apenas do novo modelo do acadêmico.)

A consulta das práticas pode ser feita a qualquer momento do dia ou do período letivo previamente cadastrado*, basta fazer uma requisição do tipo POST.

## Variáveis

| variável | tipo | Descrição |
| ------ | ------ |------ |
| token | string | Token gerado pela nossa equipe para sua instituição. Basta requisitar o token pelo e-mail [email protected] ou entrar em contato diretamente pelo contato (61) 99232-9091. |
| discine_code | string | Codigo dá turma/disciplina consultada |

## Retorno da requisição 

> url:https://instancia.bonsae.com.br/api/webhook/practice

*“instancia” na URL acima se refere ao nome da IES, campus ou unidade que a insituição irá implantar a Bonsae. De acordo com a quantidade de campus, a URL pode ter um ou dois formatos. Exemplo de formatos.: "unit.bonsae.com.br" ou "unit.aracaju.bonsae.com.br". Confirme com a coordenação do curso ou com a própria equipe Bonsae qual dos dois formatos será utilizado para o seu caso específico.

```sh
{
	"name": "turma 1",
	"code": "1915b",
	"practices": [
		{
			"students": [
				{
					"name": "aluno",
					"registration_number": null,
					"email": "aluno@bonsae.com",
					"cpf": null,
					"workload_real": "00:00:00",
					"workload_simulated": null,
					"grade": null,
					"presence": 0,
					"observations": null
				}
			],
			"is_simulated": 1,
			"name": "prática 1",
			"start_date": "2022-06-28",
			"end_date": "2022-07-01",
			"grade": 10,
			"practice_type_id": 1,
			"type": "Aps"
		},
		{
			"students": [
				{
					"name": "aluno",
					"registration_number": null,
					"email": "aluno@bonsae.com",
					"cpf": null,
					"workload_real": "00:00:00",
					"workload_simulated": null,
					"grade": null,
					"presence": 0,
					"observations": null
				}
			],
			"is_simulated": 1,
			"name": "fsagfasgasdgfa",
			"start_date": "2022-06-28",
			"end_date": "2022-07-01",
			"grade": 10,
			"practice_type_id": 1,
			"type": "Aps"
		},
	]
}
```

| variável | tipo | Descrição |
| ------ | ------ |------ |
| students | array | Array de alunos |
| students[name] | string | Nome do aluno |
| students[registration_number] | string | Matrícula do aluno |
| students[email] | string | Email do aluno |
| students[cpf] | string | CPF do aluno |
| students[workload_real] | string | Carga hóraria acumulada de práticas reais |
| students[workload_simulated] | string | Carga hóraria acumulada de práticas simuladas |
| students[grade] | string | Nota do aluno nas práticas (Prática Acadêmica, APS, Evento Acadêmico ou Projeto) |
| students[presence] | string | Presença do aluno |
| students[observations] | string | Feedback que o professor deu sobre a prática do aluno |
| is_simulated | Boolean | Tipo da prática (simulada ou real) |
| name | String | Nome da prática |
| start_date | Date | Data inicial da prática |
| end_date | Date | Data final da prática |
| grade | float | Pontuação máxima da prática |
| type | array | Tipo da prática (Aps, Prática Acadêmica, Evento Acadêmico ou Projeto) |

