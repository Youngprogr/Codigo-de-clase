# Codigo-de-clase
class paciente:
    edad = 0

    sexo = ''

    tipo = ''

    nivel = ''

    # Constructor

    def __init__(self, edad, sexo, tipo, nivel):
        self.edad = edad

        self.sexo = sexo

        self.tipo = tipo

        self.nivel = nivel

    def getedad(self):
        return self.edad

    def getsexo(self):
        return self.sexo

    def gettipo(self):
        return self.tipo

    def getnivel(self):
        return self.nivel


def validaedad():
    edad = 0

    while (edad < 18 or edad > 75):
        edad = int(input("Ingrese la edad (18 a 75): "))

    return edad


e = 0

listap = []

while (e != -1):

    e = validaedad()

    if (e != -1):
        s = input("Ingrese el sexo (F o M): ")

        t = input("Ingrese el tipo (R: Renal, H: Hepático, C:Covid): ")

        n = input("Ingrese el nivel (B: Bueno, R: Regular, M: Malo): ")
    

        # Creo un objeto de la clase paciente

        p = paciente(e, s, t, n)

        # Agregando el objeto a la lista (es una lista de pacientes)

        listap.append(p)

# a) ¿Cuántos pacientes son adultos mayores (adulto mayor es quien tiene 60 o más años)?

cedad = 0

for x in listap:

    # x = p

    if (x.getedad() >= 60):
        cedad = cedad + 1

print("La cantidad de mayores de 60 años es: ", cedad)

# b) ¿Cuál es el promedio de edad de los pacientes que solicitaron una prueba COVID?

cpc = 0  # contador de pruebas covid

sumaedad = 0  # suma edad de pacientes con prueba covid

for x in listap:

    if (x.gettipo() == 'C'):
        cpc = cpc + 1

        sumaedad = sumaedad + x.getedad()

print("El promedio de edad de pacientes con prueba Covid es: ", sumaedad / cpc)

# c) ¿Cuál es el nivel o niveles de satisfacción que tienen una mayor frecuencia?

conB = 0

conR = 0

conM = 0

for x in listap:

    if (x.getnivel() == 'B'):
        conB = conB + 1

    if (x.getnivel() == 'R'):
        conR = conR + 1

    if (x.getnivel() == 'M'):
        conM = conM + 1

print("El nivel con mayor satisfacción es: ")

print("Bueno: ", conB)

print("Regular: ", conR)

print("Malo: ", conM)

if (conB > conR and conB > conM):
    print("Bueno: ", conB)

if (conR > conB and conR > conM):
    print("Regular: ", conR)

if (conM > conB and conM > conR):
    print("Malo: ", conM)

if (conB == conR and conB == conM):
    print("Bueno: ", conB)

    print("Regular: ", conR)

    print("Malo: ", conM)

# d) ¿Cuál es la edad de la mujer más joven que no se realizó una prueba COVID?

edadM = 100

for x in listap:

    if (x.getsexo() == 'F' and x.gettipo() != 'C'):

        if (x.getedad() < edadM):
            edadM = x.getedad()

print("La edad de la Mujer más joven es: ", edadM)
