# Ejemplos-de-SOLID
Estos son algunos ejemplos de los principios SOLID

Ejemplo del principio de responsabilidad unica

def medir_area(base, altura, figura):
  if figura == 'cuadrado':
    return base * altura
  elif figura == 'triangulo':
    return base * altura / 2

Como vemos, esta funcion se encarga de calcular el area de DOS figuras: el triangulo y el rectangulo.

Esta funcion rompe el primer principio de SOLID ya que tiene dos razones para existir: calcular el area del triangulo y del rectangulo.

Para poder hacer este codigo guiandonos del primer principio tenemos que separarlo en dos funciones diferentes para que asi
las dos tengan una sola razon para estar en nuestro codigo, es decir, una sola responsabilidad. EJ:

def medir_area_cuadrado(base, altura):
  return base * altura
  
def medir_area_triangulo(base, altura):
  return base * altura / 2
  
Ejemplo del principio Abierto - Cerrado

def medir_area(base, altura, figura):
  if figura == 'cuadrado':
    return base * altura
  elif figura == 'triangulo':
    return base * altura / 2
    
Que pasaria si quisieramos agregar una nueva funcionalidad a este codigo?

por ejemplo, calcular el area del circulo.

Tendriamos que hacer esto:

def medir_area(base, altura, radio = None, figura):
  if figura == 'cuadrado':
    return base * altura
  elif figura == 'triangulo':
    return base * altura / 2
  elif figura == 'circulo':
    return 3.14 * radio**2

Aqui estariamos modificando la funcion existente y por lo tanto rompiendo el segundo principio.

Mi codigo tiene que estar abierto a la extension pero cerrado a modificacion.

Para poder hacerlo de acuerdo al segundo principio tenemos que tenerlo de acuerdo al primer principio:

def medir_area_cuadrado(base, altura):
  return base * altura
  
def medir_area_triangulo(base, altura):
  return base * altura / 2
  
Y asi podemos EXTENDER nuestro codigo y no tener que MODIFICARLO agregando la otra funcion:

def medir_area_cuadrado(base, altura):
  return base * altura
  
def medir_area_triangulo(base, altura):
  return base * altura / 2
  
def medir_area_circulo(radio):
  return 3.14 * radio**2
