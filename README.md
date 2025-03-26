############ Sistema Bancário CaioSoares ############

senha_correta = "A121314."  
tentativas = 3  

while tentativas > 0:
    senha = input("Digite a sua senha: ")
    if senha == senha_correta:
        print("Acesso concedido! Bem-vindo ao Banco CaioSoares !.")
        break
    else:
        tentativas -= 1
        print(f"Senha incorreta! Você tem {tentativas} tentativa(s) restante(s).")

if tentativas == 0:
    print("Número máximo de tentativas excedido. Encerrando o programa.")
    exit()


menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou!  Saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.Voce so tem direito a 3 saques por dia.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! Valor informado é inválido.")

    elif opcao == "e":
        print("\n= EXTRATO =")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "q":
        break

    else:
        print("Operação indisponivel,  favor selecione novamente a operação desejada.")

