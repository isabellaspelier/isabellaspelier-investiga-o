# isabellaspelier-investiga-o
# 🕵️ Operação Código Fantasma

## Investigação de um Crime Digital

Na noite de 14 de setembro, o sistema acadêmico do Colégio Horizonte apresentou uma atividade suspeita.

Algumas informações de alunos foram alteradas e um arquivo administrativo desapareceu do sistema.

A equipe responsável pela tecnologia da escola analisou os registros de acesso e descobriu que várias pessoas tinham utilizado os computadores naquele dia.

### Objetivo da investigação

Descobrir:

- Quem realizou o acesso suspeito?
- Em qual horário ocorreu?
- Qual computador foi utilizado?
- Qual foi a possível motivação?
- Quais evidências comprovam a conclusão?

### Suspeitos

**Lucas Almeida**
Aluno do 3º ano e com conhecimento básico de programação.

**Marina Costa**
Aluna do 2º ano e participante do clube de tecnologia.

**Rafael Martins**
Funcionário da secretaria com acesso administrativo.

**Gabriel Souza**
Aluno do 3º ano que utilizava frequentemente os computadores do laboratório.

### Como executar

É necessário ter Python instalado.

Execute:

```bash
python src/investigacao.py
---

### `src/investigacao.py`

```python
import csv
import os

BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
ARQUIVO_ACESSOS = os.path.join(BASE_DIR, "dados", "acessos.csv")


def carregar_acessos():
acessos = []

with open(ARQUIVO_ACESSOS, "r", encoding="utf-8") as arquivo:
leitor = csv.DictReader(arquivo)

for linha in leitor:
acessos.append(linha)

return acessos


def mostrar_acessos():
acessos = carregar_acessos()

print("\n===== REGISTROS DE ACESSO =====\n")

for acesso in acessos:
print(
f"Data: {acesso['data']} | "
f"Horário: {acesso['horario']} | "
f"Usuário: {acesso['usuario']} | "
f"Computador: {acesso['computador']} | "
f"Ação: {acesso['acao']}"
)


def analisar_suspeitos():
print("\n===== SUSPEITOS =====\n")

print("1. Lucas Almeida")
print(" Aluno do 3º ano. Conhecimento básico de programação.")

print("\n2. Marina Costa")
print(" Aluna do 2º ano. Participa do clube de tecnologia.")

print("\n3. Rafael Martins")
print(" Funcionário da secretaria. Possui acesso administrativo.")

print("\n4. Gabriel Souza")
print(" Aluno do 3º ano. Frequentava o laboratório de informática.")


def procurar_inconsistencias():
acessos = carregar_acessos()

print("\n===== INCONSISTÊNCIAS ENCONTRADAS =====\n")

encontrado = False

for acesso in acessos:
if acesso["computador"] == "LAB-07" and acesso["horario"] == "18:42":
print("⚠️ Acesso suspeito encontrado!")
print(f"Horário: {acesso['horario']}")
print(f"Usuário registrado: {acesso['usuario']}")
print(f"Computador: {acesso['computador']}")
print(f"Ação: {acesso['acao']}")
encontrado = True

if not encontrado:
print("Nenhuma inconsistência encontrada.")


def mostrar_evidencias():
print("\n===== EVIDÊNCIAS =====\n")

print("EVIDÊNCIA 01")
print("O computador LAB-07 aparece como utilizado às 18:42.")

print("\nEVIDÊNCIA 02")
print("O registro de manutenção indica que o LAB-07 deveria estar desligado.")

print("\nEVIDÊNCIA 03")
print("Uma testemunha informou que Gabriel permaneceu no laboratório após o horário normal.")

print("\nEVIDÊNCIA 04")
print("O arquivo alterado foi modificado poucos minutos depois do acesso.")


def mostrar_conclusao():
print("\n===== CONCLUSÃO DA INVESTIGAÇÃO =====\n")

print("Após comparar os registros e as evidências,")
print("o principal suspeito é Gabriel Souza.")
print()
print("O motivo da suspeita é sua presença no laboratório")
print("próximo ao horário do acesso registrado no computador LAB-07.")
print()
print("A conclusão é baseada apenas nas evidências fictícias")
print("criadas para este projeto escolar.")


def menu():
while True:
print("\n")
print("======================================")
print(" OPERAÇÃO CÓDIGO FANTASMA")
print("======================================")
print("1 - Ver registros de acesso")
print("2 - Analisar suspeitos")
print("3 - Procurar inconsistências")
print("4 - Ver evidências")
print("5 - Ver conclusão")
print("0 - Sair")
print("======================================")

opcao = input("Escolha uma opção: ")

if opcao == "1":
mostrar_acessos()

elif opcao == "2":
analisar_suspeitos()

elif opcao == "3":
procurar_inconsistencias()

elif opcao == "4":
mostrar_evidencias()

elif opcao == "5":
mostrar_conclusao()

elif opcao == "0":
print("\nInvestigação encerrada.")
break

else:
print("\nOpção inválida. Tente novamente.")


if __name__ == "__main__":
menu()