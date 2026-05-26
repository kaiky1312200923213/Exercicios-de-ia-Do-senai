# Exercicios-de-ia-Do-senai
exercício 1:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

pergunta = input("Você: ")

resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um assistente prestativo."
        },
        {
            "role": "user",
            "content": pergunta
        }
    ]
)

print("IA:", resposta.choices[0].message.content)
execicio 2:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

pergunta = input("Você: ")

resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um professor de programação especialista em Python. Explique os conceitos de forma simples e didática, com exemplos de código quando necessário. Use linguagem fácil para iniciantes entenderem."
        },
        {
            "role": "user",
            "content": pergunta
        }
    ]
)

print("Professor:", resposta.choices[0].message.content)
exercicio3:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

print("=== IA Personagem ===")
print("Escolha um personagem:")
print("1 - Pirata")
print("2 - Astronauta")
print("3 - Ninja")
print("4 - Robô")

escolha = input("\nDigite o número: ")

personagens = {
    "1": ("Pirata",     "Você é um pirata do século XVII. Fale sempre como um pirata, usando expressões como 'Arrr!', 'Por Davy Jones!', 'Navegar os mares!'. Responda qualquer pergunta mantendo o personagem de pirata."),
    "2": ("Astronauta", "Você é um astronauta experiente que já viajou pelo espaço. Fale sempre relacionando tudo ao espaço, gravidade zero, galáxias e missões espaciais. Use termos como 'Houston', 'órbita', 'missão'."),
    "3": ("Ninja",      "Você é um ninja misterioso e sábio do Japão antigo. Fale de forma calma e filosófica, com sabedoria e mistério. Use expressões como 'nas sombras', 'a mente é a maior arma', 'o silêncio fala mais alto'."),
    "4": ("Robô",       "Você é um robô. Fale de forma mecânica e lógica, como se fosse uma máquina processando informações. Use expressões como 'PROCESSANDO...', 'DADOS ANALISADOS', 'CÁLCULO CONCLUÍDO'. Seja preciso e direto.")
}

if escolha not in personagens:
    print("Opção inválida!")
else:
    nome, system = personagens[escolha]
    print(f"\nVocê escolheu: {nome}")
    print("-" * 30)

    pergunta = input("Você: ")

    resposta = cliente.chat.completions.create(
        model="meta/llama-3.1-8b-instruct",
        messages=[
            {
                "role": "system",
                "content": system
            },
            {
                "role": "user",
                "content": pergunta
            }
        ]
    )

    print(f"\n{nome}: {resposta.choices[0].message.content}")
execicio4:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

print("=== Gerador de Histórias ===\n")

personagem = input("Nome do personagem: ")
tema = input("Tema da história: ")

resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um contador de histórias criativo. Crie histórias curtas, divertidas e envolventes com no máximo 5 parágrafos."
        },
        {
            "role": "user",
            "content": f"Crie uma pequena história com o personagem chamado '{personagem}' e o tema '{tema}'."
        }
    ]
)

print("\n=== Sua História ===\n")
print(resposta.choices[0].message.content)
exercício 5:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

print("=== Tradutor com IA ===\n")

texto = input("Texto para traduzir: ")
idioma = input("Traduzir para qual idioma: ")

resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um tradutor profissional. Traduza o texto exatamente como pedido, sem explicações extras. Retorne apenas o texto traduzido."
        },
        {
            "role": "user",
            "content": f"Traduza o seguinte texto para {idioma}: '{texto}'"
        }
    ]
)

print(f"\nTradução ({idioma}):")
print(resposta.choices[0].message.content)
execicio6:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

print("=== Explicador de Palavras ===\n")

palavra = input("Digite uma palavra: ")

resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um professor didático que explica palavras de forma simples e fácil de entender. Explique o significado da palavra como se estivesse falando com uma criança de 10 anos. Use exemplos do dia a dia para ajudar na explicação."
        },
        {
            "role": "user",
            "content": f"Explique o significado da palavra: '{palavra}'"
        }
    ]
)

print(f"\nSignificado de '{palavra}':")
print(resposta.choices[0].message.content)
exercício 7:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

print("=== Quiz com IA ===\n")

# Passo 1 — IA cria uma pergunta
pergunta_resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um professor que cria perguntas de quiz. Crie apenas UMA pergunta de conhecimentos gerais. Retorne somente a pergunta, sem resposta, sem numeração, sem explicação."
        },
        {
            "role": "user",
            "content": "Crie uma pergunta de conhecimentos gerais para um quiz."
        }
    ]
)

pergunta = pergunta_resposta.choices[0].message.content
print(f"Pergunta: {pergunta}\n")

# Passo 2 — Usuário responde
resposta_aluno = input("Sua resposta: ")

# Passo 3 — IA avalia a resposta
avaliacao = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um professor que avalia respostas de quiz. Diga se a resposta do aluno está correta ou errada, explique o porquê e dê a resposta certa de forma simples e animada."
        },
        {
            "role": "user",
            "content": f"Pergunta: {pergunta}\nResposta do aluno: {resposta_aluno}\nA resposta está correta?"
        }
    ]
)

print(f"\nResultado:")
print(avaliacao.choices[0].message.content)
exercício 8:
from openai import OpenAI

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

print("=== Treinador Motivacional ===")
print("Fale como você está se sentindo!\n")

sentimento = input("Você: ")

resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um treinador motivacional animado e positivo. Sempre responda com energia, entusiasmo e palavras de incentivo. Use frases motivadoras, elogios e dicas práticas para animar o usuário. Nunca seja negativo. Termine sempre com uma frase de encorajamento."
        },
        {
            "role": "user",
            "content": sentimento
        }
    ]
)

print(f"\nTreinador: {resposta.choices[0].message.content}")
exercício 9:
from gtts import gTTS

print("=== Texto para Fala ===\n")

texto = input("Digite o texto: ")

audio = gTTS(text=texto, lang="pt")

audio.save("fala.mp3")

print("\nÁudio salvo como fala.mp3!")
exercício 10:
from openai import OpenAI
from gtts import gTTS

API_KEY = "SUA_API_KEY_AQUI"

cliente = OpenAI(
    api_key=API_KEY,
    base_url="https://integrate.api.nvidia.com/v1"
)

print("=== IA com Voz ===\n")

pergunta = input("Você: ")

resposta = cliente.chat.completions.create(
    model="meta/llama-3.1-8b-instruct",
    messages=[
        {
            "role": "system",
            "content": "Você é um assistente prestativo. Responda de forma clara e objetiva em português."
        },
        {
            "role": "user",
            "content": pergunta
        }
    ]
)

texto = resposta.choices[0].message.content

print(f"\nIA: {texto}")

audio = gTTS(text=texto, lang="pt")
audio.save("resposta.mp3")

print("\nÁudio salvo como resposta.mp3!")
