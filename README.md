# TED
Trabalho feito pela dupla: Elielson R. e Luis Henrique

import sys
def mdc(a, b):
    if b == 0:
        return a
    return mdc(b, a % b)

def soma_digitos(n):
    if n == 0:
        return 0
    return n % 10 + soma_digitos(n // 10)

def main():
    data = sys.stdin.read().split('\n')
    q = int(data[0].strip())
    saida = []
    for i in range(1, q + 1):
        linha = data[i].strip() if i < len(data) else ""
        partes = linha.split()
        if not partes:
            saida.append("ERRO: OperacaoInvalida")
            continue

        op = partes[0]

        if op == 'M':
            if len(partes) != 3:
                saida.append("ERRO: EntradaInvalida")
                continue
            try:
                a = int(partes[1])
                b = int(partes[2])
            except ValueError:
                saida.append("ERRO: EntradaInvalida")
                continue
            if a <= 0 or b <= 0:
                saida.append("ERRO: EntradaInvalida")
                continue
            saida.append(f"MDC = {mdc(a, b)}")

        elif op == 'S':
            if len(partes) != 2:
                saida.append("ERRO: EntradaInvalida")
                continue
            try:
                n = int(partes[1])
            except ValueError:
                saida.append("ERRO: EntradaInvalida")
                continue
            if n < 0:
                saida.append("ERRO: EntradaInvalida")
                continue
            saida.append(f"SOMA = {soma_digitos(n)}")

        else:
            saida.append("ERRO: OperacaoInvalida")

    print('\n'.join(saida))

if __name__ == "__main__":
    main()
