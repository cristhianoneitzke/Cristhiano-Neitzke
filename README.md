class ContaBancaria:
    def __init__(self, titular, saldo = 0):
        self._titular = titular
        self._saldo = saldo

    def depositar(self, valor):
        if valor > 0:
            self._saldo += valor
            print (f'deposito de R${valor} realizado com sucesso')
        
        else:
            print ('valor invalido')

    def sacar(self, valor):
        if 0 < valor <= self.saldo:
            self._saldo -= valor
            print(f'saque de R$ {valor} realizado com sucesso')
        
        else:
            print ('saque invalido')

    def transferir(self, destino, valor):
        if self._saldo >= valor > 0:
            self._saldo -= valor
            destino.depositar(valor)
            print (f'transferencia de R${valor} para {destino.titular} realizado com sucesso')

        else:
            print('transferencia negada')
    
    def extrato(self):
        print(f'titular: {self._titular}')
        print(f'saldo: R${self._saldo}')
    
