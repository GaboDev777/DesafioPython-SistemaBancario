# DesafioPython-SistemaBancario
Este projeto simula um sistema bancário básico, executado em um console, permitindo ao usuário realizar operações como depósitos, saques, consultas de saldo, visualização de extratos e logout do sistema.

menu = '''
#####MENU#####

CONSULTAR [0]
DEPOSITAR [1]
SACAR     [2]
EXTRATO   [3]
SAIR      [4]

'''

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
limite_saques = 3

while True:

    opcao = input(menu)

    if opcao == "1":
        valor = float(input("Informe o valor do deposito: "))

        if valor > 0:
            saldo += valor
            extrato += f"deposito: R$ {valor: .2f}\n"

        else:
            print("Operaçao falhou! Valor informado é invalido.")

    elif opcao == "2":
        valor = float(input("Informe o valor do saque: "))

        excede_saldo = valor > saldo

        excede_limite = valor > limite

        excede_saques = numero_saques >= limite_saques

        if excede_saldo:
            print("operação falhou, voce nao tem saldo suficiente.")

        if excede_limite:
            print("operação falhou, o valor do saque excede o limite.")

        if excede_saques:
            print("operação falhou, voce ja atingiu o limite de saque diario.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor: .2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! Valor informado é inválido.")

    elif opcao == "3":
        print("\n====== EXTRATO ======")
        print(extrato if extrato else "Não foram realizadas movimentações.")
        print(f"Saldo atual: R$ {saldo:.2f}")
        print("======================\n")

    elif opcao == "0":
        print(f"\nSeu saldo atual é: R$ {saldo:.2f}\n")

    elif opcao == "4":
        print("\nSaindo do sistema... Volte sempre!")
        break

    else:
        print("Opção inválida! Tente novamente.")
