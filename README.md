# Sistema-simples-de-conta-b-ncaria
# Menu de  opção  de escolha do usuário
menu = """

[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair

=> """

saldo = 0                 # Valorr do  saldo inicial
limite = 500
extrato = ""
numero_saques = 0         # Contador de saque
LIMITE_SAQUES = 3         # Limite de saque

# Laço para a definição da escolha do usuário

while True:

    opcao = int(input(menu))

# Condições conforme a escollha do usuário

    if opcao == 1:               # Opção para depósito
        valor = float(input("Informe o valor do depósito: R$ "))

        if valor > 0:
            print('Deposito realizado com sucesso !')
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == 2:        # Opção para saque(informar o valor do saque)
        valor = float(input("Informe o valor do saque: R$ "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

    # Exibe a mensagen se não digitado conforme as condições de saque

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == 3:           # Exibe o extrato da conta do usuário
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == 4:         # Opção para quebrar o laço e sair do menu
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")      # Se não for escolhido nenhuma das opções do menu, repete o laço
