# examen
# Primera actualización realizada en Visual Studio Code
productos={'8475HD': ['HP', 15.6, '8GB', 'DD', '1T', 'Intel Core i5', 'Nvidia GTX1050'],
            '2175HD': ['Acer', 14, '4GB', 'SSD', '512GB', 'Intel Core i5', 'Nvidia GTX1050'],
            'JjfFHD': ['Asus', 14, '16GB', 'SSD', '256GB', 'Intel Core i7', 'Nvidia RTX2080Ti'],
            'fgdxFHD': ['HP', 15.6, '8GB', 'DD', '1T', 'Intel Core i3', 'integrada'],
            'GF75HD': ['Asus', 15.6, '8GB', 'DD', '1T', 'Intel Core i7', 'Nvidia GTX1050'],
            '123FHD': ['Acer', 14, '6GB', 'DD', '1T', 'AMD Ryzen 5', 'integrada'],
            '342FHD': ['Acer', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 7', 'Nvidia GTX1050'],
            'UWU131HD': ['Dell', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 3', 'Nvidia GTX1050'],
            }
productos={'modelo': ['marca', 'pantalla', 'RAM', 'Disco', 'GB de DD', 'procesador', 'video']}

stock={'8475HD': [387990,10], '2175HD': [327990,4], 'JjfFHD': [424990,1],
         'fgdxFHD': [664990,21], '123FHD': [290890,32], '342FHD': [444990,7],
         'GF75HD': [749990,2], 'UWU131HD': [349990,1], 'FS1230HD': [249990,0],
        }
Stock= {'modelo': ['precio', 'stock']}

def menu(titulo,opciones):
    print(titulo)
    print('===========================')
    i=1
    for opc in opciones:
        print(i,'.-',opc)
        i=i+1
    print(i,'.-Salir')
    opcion=input('Ingrese Opción: ')
    return opcion

def Stock_marca(marca):
   total_stock=0
   marca=marca
   for modelo in productos:
      if productos[modelo][0].lower==marca:
         total_stock+=stock[modelo][1]
         print(f'stock total para la marca {marca}: {total_stock}')



def busqueda_ram_precio(ram_min, ram_max, precio):
   encontrado=False
   for modelo in productos:
         ram=int(productos[modelo][2])
         precio=stock[modelo][0]
         stock_disponible=stock[modelo][1]
         if ram_min<= ram <= ram_max and precio <= precio and stock_disponible >0:
            print(f'{modelo}: {productos[modelo]}, {precio}, stock: {stock_disponible}')
            encontrado=True
            print()




def eliminar_producto(modelo):
    nombre=input('Ingrese Modelo a Eliminar: ')
    for clave,valor in productos.items():
        if valor[0]==nombre:
            productos.pop(clave) 
            print('producto eliminado con exito.')
            return
    print('El modelo no Existe.')

while True:
    print('Menú Principal')
    print('''
        1. Stock marca
        2. Busqueda por RAM y precio
        3. Eliminar producto
        4. SALIR
    ''')
    opc=input('Ingrese Opción: ')
    if opc=='1':
        Stock_marca()
    elif opc=='2':
        busqueda_ram_precio()
    elif opc=='3':
        eliminar_producto()
    elif opc=='4':
        print('Gracias por preferirnos....')
        break
    else:
        print('Opción Incorrecta')
