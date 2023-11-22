import random
from Personagem import Personagem

class Guerreiro(Personagem):
    def _init_(self, nome):
        super()._init_(nome, pv =100, pa=15)

    def usarSkill(self, inimigo):
        dano = random.randint(5,10)
        print(f'{self.nome} usa habilidade especial e causa {dano} de dano')
        inimigo.perderVida(dano)

class Mago(Personagem):
    def _init_(self, nome):
        super()._init_(nome, pv =80, pa=20)

    def usarSkill(self, inimigo):
        dano = random.randint(10,20)
        print(f'{self.nome} usa habilidade especial e causa {dano} de dano')
        inimigo.perderVida(dano)

class Arqueiro(Personagem):
    def _init_(self, nome):
        super()._init_(nome, pv =90, pa=18)

    def usarSkill(self, inimigo):
        chance = random.random()
        if chance > 0.3:
            print(f'{self.nome} dale tiro veio')
            inimigo.perderVida(2 * self.pa)
        else:
            print(f'{self.nome} Erroooouuu')




import random

#pv= pontos de vida, pa= pontos de ataque, pd= pontos de dano
class Personagem:
    def _init_(self, nome, pv, pa):
        self.nome= nome
        self. __pv = pv
        self.pa = pa

    def atacar (self, inimigo):
        print(f'{self.nome} ataca')
        inimigo.perderVida(self.pa)

    def perderVida(self, pd):
        self.__pv -= pd
        if self.__pv <= 0:
            self.__pv = 0

    def estaVivo(self):
        return self.__pv >0

    def mostrarStatus(self):
        print(f'{self.nome}: PV - {self.__pv}, PA - {self.pa}')



        from Personagem import Personagem
from Classes import Guerreiro, Mago, Arqueiro

def combate(personagem1, personagem2):
    print('--------------')
    personagem1.mostrarStatus()
    personagem2.mostrarStatus()
    print('--------------')
    while personagem1.estaVivo() and personagem2.estaVivo():
        personagem1.atacar(personagem2)
        personagem2.mostrarStatus()
        personagem2.atacar(personagem1)
        personagem1.mostrarStatus()
        print('--------------')
        personagem1.usarSkill(personagem2)
        personagem2.mostrarStatus()
        personagem2.usarSkill(personagem1)
        personagem1.mostrarStatus()
        print('--------------')


guerreiro = Guerreiro('Rogerio Ceni')
mago = Mago ('Donald Tramp')
arqueiro = Arqueiro('Faustao')

combate(guerreiro, arqueiro)
print('\n --- proximo combate --- \n')

class ContaBancaria:
    def _init_(self, titular, saldo = 0):
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



        from ContaBancaria import ContaBancaria


class ContaCorrente(ContaBancaria):
    def _init_(self, titular, saldo=0, limite = 1000):
        super()._init_(titular, saldo)
        self._limite = limite

    def sacar(self, valor):
        if 0 < valor <= self._saldo + self._limite:
            self._saldo -= valor
            print (f'saque de R${valor} realizado com sucesso. ')
        else:
            print(f'saque invalido')


class ContaPoupanca(ContaBancaria):
    def _init_(self, titular, saldo=0, taxa=0.03):
        super()._init_(titular, saldo)
        self._taxa = taxa

    def aplicarJuros(self):
        juros = self._saldo * self._taxa
        self._saldo += juros
        print (f'juros de R${juros} aplicado com sucesso.')


        from ContaBancaria import ContaBancaria
from ContasTipo import ContaCorrente, ContaPoupanca

conta1 = ContaCorrente('Jorge',1000, 2000) 
conta2 = ContaPoupanca ('Purcina', 5000, 0.05)

conta1.extrato()
conta1.sacar(1500)
conta1.extrato()
conta1.transferir(conta2, 500)
conta2.aplicarJuros()
conta2.extrato()




ATIVIDADE 

1
class Pessoa:
    #construtor
    def_init_(self,nome,ideade,refeicao=false,comunicacao=false):
        self._nome = nome 
        self._idade = idade 
        self._refeicao = refeicao
        self._comunicacao = comunicacao

    #get
    @property
    def nome(self):
        return self._nome
    #set
    @nome.setter
    def nome(self,nome):
        self._nome = nome

    #get
    @property
    def idedade(self):
        return self._idade
    #set
    @idade.setter
    def idade(self,ideade):
        self._idade = idade

    #get
    @property
    def refeicao(self):
        return self._refeicao
    #set
    @refeicao.setter
    def refeicao(self,refeicao):
        self._refeicao = refeicao

    #get
    @property
        def comunicacao(self):
        return self._comunicacao
    #set
    @comunicacao.setter
    def counicacao(self,comunicacao):
        self._comunicacao = comunicacao

    #metodos 
    def falar(self,assunto):
        if self._refeicao:
            print(f'{self._nome} nao pode falar de boca cheia')
            return
        if self._comunicacao:
            print(f'{self._nome} ja esta falando')
            return
        print(f'`{self._nome} esta falando sobre {assunto}')
        self._comunicacao = True

    def pararfala(self):
        if not self._comunicacao:
            print(f'{self._nome} nao esta falando')
            return
        print(f'{self._nome} parou de falar')
        self_comunicacao = False

    def comer(self,alimento):
        if self._refeicao:
            print(f'{self._nome} ja esta comendo')
            return
        if self._comunicacao:
            print(f'{self._nome} nao pode comer falando')
            return
        print(f'{self._nome} esta comendo {alimento}')
        self._refeicao = True

    def pararcomer(self):
        if not self._refeicao
        print('f{self._nome} nao esta comendo')
        return
    print(f'{self._nome} parou de comer')
    self._refeicao = false



  2
  import random

# Listas de nomes e sobrenomes
nomes = ["Ana", "João", "Maria", "Pedro", "Luísa", "Rafael", "Lara", "Carlos", "Eva", "Lucas",
         "Lívia", "Bruno", "Juliana", "Rodrigo", "Mariana", "Fernando", "Camila", "Daniel", "Patrícia"]
sobrenomes = ["Silva", "Santos", "Oliveira", "Pereira", "Ferreira", "Rodrigues", "Almeida", "Lima", "Souza", "Costa",
              "Carvalho", "Gonçalves", "Ribeiro", "Araújo", "Martins", "Cavalcanti", "Freitas", "Correia", "Vieira"]

def gera_dados_aleatorios(N):
    with open("dados_pessoais.txt", "w") as arquivo:
        for _ in range(N):
            nome_completo = f"{random.choice(nomes)} {random.choice(sobrenomes)}"
            idade = random.randint(18, 60)
            altura = round(random.uniform(1.50, 2.00), 2)
            arquivo.write(f"{nome_completo}, {idade} anos, {altura} m\n")

N = int(input("Digite o número de registros a serem gerados: "))
gera_dados_aleatorios(N)


def escreverNumerosAleatorios(qtdNumeros, nomeArquivo):
    arquivoNumeros = open(nomeArquivo, 'w')
    for i in range(qtdNumeros):
        nome_completo = f"{random.choice(nomes)} {random.choice(sobrenomes)}"
        idade = random.randint(18, 60)
        altura = round(random.uniform(1.50, 2.00), 2)
        arquivoNumeros.write(f"{nome_completo}, {idade} anos, {altura} m\n")
    arquivoNumeros.close()

escreverNumerosAleatorios(100, 'cadastro.txt')



3

def copia_arquivo_sem_comentarios(origem, destino):
    with open(origem, "r") as arquivo_origem, open(destino, "w") as arquivo_destino:
        for linha in arquivo_origem:
            if not linha.strip().startswith("//"):
                arquivo_destino.write(linha)

copia_arquivo_sem_comentarios("arquivo_origem.txt", "arquivo_destino.txt")


4

def calcular_media(notas):
    notas = [float(nota) for nota in notas.split()]
    return sum(notas) / len(notas)

def gerar_arquivo_medias(nome_alunos, nome_notas, nome_resultado):
    with open(nome_alunos, "r") as arquivo_alunos, open(nome_notas, "r") as arquivo_notas, open(nome_resultado, "w") as arquivo_resultado:
        for linha_aluno, linha_notas in zip(arquivo_alunos, arquivo_notas):
            nome_aluno = linha_aluno.strip()
            media = calcular_media(linha_notas)
            arquivo_resultado.write(f"{nome_aluno}: {media}\n")

gerar_arquivo_medias("alunos.txt", "notas.txt", "medias.txt")



5

def alterar_nota_aluno(arquivo_notas, nome_aluno, nota_antiga, nova_nota):
    linhas = []
    with open(arquivo_notas, "r") as arquivo_leitura:
        for linha in arquivo_leitura:
            if nome_aluno in linha:
                linha = linha.replace(nota_antiga, nova_nota)
            linhas.append(linha)
    with open(arquivo_notas, "w") as arquivo_escrita:
        arquivo_escrita.writelines(linhas)

alterar_nota_aluno("notas.txt", "João", "7.5", "8.0")


6


def separar_enderecos_ip(arquivo_entrada, arquivo_validos, arquivo_invalidos):
    with open(arquivo_entrada, "r") as entrada, open(arquivo_validos, "w") as validos, open(arquivo_invalidos, "w") as invalidos:
        for linha in entrada:
            endereco = linha.strip().split(".")
            if len(endereco) == 4:
                octetos_validos = True
                for octeto in endereco:
                    if not (octeto.isdigit() and 0 <= int(octeto) <= 255):
                        octetos_validos = False
                        break
                if octetos_validos:
                    validos.write(linha)
                else:
                    invalidos.write(linha)
            else:
                invalidos.write(linha)

# Exemplo de uso
separar_enderecos_ip("enderecos.txt", "validos.txt", "invalidos.txt")
