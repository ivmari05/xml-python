#
**Introducción a Python y XML**
#

![Alt](dd.jpeg)

Contenido

¿Qué es XML?

Trabajando con XML en Python

El módulo xml.etree.ElementTree

El módulo xml.dom.minidom

Ejemplos de Código

Links
#
*¿Qué es XML?*
#
XML es un lenguaje de marcado que se utiliza para almacenar y transportar datos de forma estructurada. Es utilizado en las webs para el intercambio de datos entre sistemas.
#
*Trabajando con XML en Python*
#
Existen varias formas de trabajar con XML en Python,las más comunes son los módulos xml.etree.ElementTree y xml.dom.minidom.
#
*El módulo xml.etree.ElementTree*
#
Este módulo proporciona una forma simple y eficiente de manipular y analizar datos XML en Python.

Ejemlo:


```
import xml.etree.ElementTree as ET

# Cargar el archivo XML
tree = ET.parse('archivo.xml')
root = tree.getroot()

# Acceder a elementos y atributos
for child in root:
    print(child.tag, child.attrib)
```

Y el módulo xml.dom.minidom
minidom es otro módulo incorporado en Python que permite trabajar con XML utilizando el DOM (Document Object Model). 

Ejemlo:


```
import xml.dom.minidom as minidom

# Cargar el archivo XML
doc = minidom.parse('archivo.xml')

# Obtener el elemento raíz
root = doc.documentElement

# Acceder a elementos
items = doc.getElementsByTagName('item')
for item in items:
    print(item.firstChild.nodeValue)
```
#
*Ejemplos de Código*
#
Aqui hay algunos ejemplos de código para ver cómo trabajar con XML en Python:

*Crear un documento XML desde cero:*

```
import xml.etree.ElementTree as ET

# Crear el elemento raíz
root = ET.Element("productos")

# Crear subelementos
producto1 = ET.SubElement(root, "producto")
producto1.set("id", "1")
nombre1 = ET.SubElement(producto1, "nombre")
nombre1.text = "Laptop"
precio1 = ET.SubElement(producto1, "precio")
precio1.text = "1000"

# Crear un árbol a partir del elemento raíz y guardar en un archivo
tree = ET.ElementTree(root)
tree.write("productos.xml")
```
#
Leer y modificar un archivo XML existente
#
```
import xml.etree.ElementTree as ET

# Cargar el archivo XML
tree = ET.parse('productos.xml')
root = tree.getroot()

# Modificar datos
for producto in root.iter('producto'):
    precio = producto.find('precio')
    nuevo_precio = float(precio.text) * 1.1
    precio.text = str(nuevo_precio)

# Guardar los cambios
tree.write('productos_modificados.xml')
```

Documentación oficial de Python sobre XML Processing

*Link:*
#	
[W3Schools sobre XML](https://www.w3schools.com/xml/default.asp "W3Schools sobre XML")
#