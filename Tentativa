from Veiculo import Veiculo

class Carro(Veiculo):
    def __init__(self, modelo, ano, cambio):
        super().__init__(tipo = "Carro", velocidade=200)
        self._modelo = modelo
        self._ano = ano
        self._cambio = cambio

    def andar(self):
        print (f"{self._tipo} {self._modelo} ano {self._ano} anda a {self._velocidade} km/h")

    def trocarMarcha(self):
        print (f'{self._tipo} {self._modelo} troca marcha de modo {self._cambio}')

    def descricao(self):
        print (f'{self._tipo}, {self._modelo}, {self._ano}, {self._cambio}, muito elegante')
