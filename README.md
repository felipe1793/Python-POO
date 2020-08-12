# Python-POO
Atividade Continua de LP2

Codigo:

class Elevador:

    andar_atual = None
    __atendidos = []
    __capacidade = None     
    __quantidade_pessoas = None 


    def __init__(self, capacidade, lista_de_andares_atendidos):
        self.__capacidade = capacidade
        self.__atendidos = lista_de_andares_atendidos
        self.andar_atual = 0
        self.__quantidade_pessoas = 0


    def entrar(self):                                       
        if self.__quantidade_pessoas < self.__capacidade:
            self.__quantidade_pessoas += 1
        else:
            print('elevador cheio')


    def sair(self):                                         
        if self.__quantidade_pessoas == 0:
            print('elevador vazio')
        else:
            self.__quantidade_pessoas -= 1


    def subir(self):                                        
        if self.andar_atual == max(self.__atendidos):
            print('Ultimo andar')
        else:
            certo = 0
            for andar in self.__atendidos:
                if self.andar_atual == andar:
                    certo = self.__atendidos.index(andar)
                    self.__atendidos.remove(andar)
                    self.andar_atual = self.__atendidos[certo]           


    def descer(self):                                       
        if self.andar_atual == min(self.__atendidos):
            print('Ultimo andar')
        else:
            certo = 0
            self.__atendidos.reverse()
            for andar in self.__atendidos:
                if self.andar_atual == andar:
                    certo = self.__atendidos.index(andar)
                    self.__atendidos.remove(andar)
                    self.andar_atual = self.__atendidos[certo]


    def deslocar_para(self, andar):                         
        for i in self.__atendidos:
            if i == andar:
                self.andar_atual = andar
            else:
                self.andar_atual = self.andar_atual


class Predio:
    __elevadores = []
    __andar_alto = None
    __andar_baixo = None


    def __init__(self, andar_alto, andar_baixo, elevadores):
        self.__andar_alto = andar_alto
        self.__andar_baixo = andar_baixo
        self.__elevadores = elevadores


    def chamar(self, andar):                                
        caixa = 0
        for elevators in range (len(self.__elevadores)):
            caixa = elevators
            if self.__elevadores[caixa].andar_atual == andar:
                self.__elevadores[caixa].andar_atual = andar
            elif self.__elevadores[caixa].andar_atual > andar:
                self.__elevadores[caixa].andar_atual = andar
            elif self.__elevadores[caixa].andar_atual < andar:
                self.__elevadores[caixa].andar_atual = andar


    def embarque(self, indice_elevador):                    
        if self.__elevadores[indice_elevador].andar_atual > 0:
            self.__elevadores[indice_elevador].entrar()          


    def desembarque(self, indice_elevador):                 
        if self.__elevadores[indice_elevador].andar_atual <= 0:
            self.__elevadores[indice_elevador].__quantidade_pessoas = 0
