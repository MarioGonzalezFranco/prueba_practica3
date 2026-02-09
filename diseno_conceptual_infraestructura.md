# Pr�ctica - Dise�o Conceptual de Infraestructura de Servidores
## Unidad 2: Infraestructura de servidores


## 1. Integrantes del grupo
Carlos Ernesto Castillo Aguirre – CA100922'
Wendy Cristabel Hernández Urías – HU10022'
Mario Enrique Gonzalez Franco – GF100822'
Francisco Isaac Gálvez Acevedo - GA100422'
Bryan Gerardo Rodriguez Rodriguez - RR101221
---

## 2. Introducci�n

En este documento se presenta el dise�o conceptual de una infraestructura de servidores, elaborado a partir de requerimientos previamente analizados y priorizados.
El objetivo es proponer una arquitectura l�gica de alto nivel que permita visualizar los componentes necesarios y su relaci�n, sin considerar marcas, modelos ni configuraciones espec�ficas.

---

## 3. Requerimientos considerados

A continuaci�n se listan los requerimientos del negocio que se tomaron como base para el dise�o conceptual.

### Requerimiento 1
**Descripci�n:** El sistema debe permitir el acceso simultáneo de usuarios desde la oficina central y tres sucursale, garantizando disponibilidad y continuidad del servicio.

### Requerimiento 2
**Descripci�n:** El sistema debe garantizar la integridad, persistencia y confiabilidad de los documentos administrativos y registros del cliente, evitando la perdida, corrupción o sobrescritura accidental de información.

---

## 4. Identificaci�n de servidores por rol

A partir de los requerimientos, se identifican los siguientes roles de servidores:

| Requerimiento | Rol del servidor | Justificaci�n |
|--------------|-----------------|---------------|
| Req. 1 | Servidor Web | Permite gestionar las solicitudes de los usuarios y distribuir el acceso al sistema, evitando sobrecarga en los componentes principales |
| Req. 2 | Servidor de Bases de Datos| Almacena la información sensible de forma controlada y separada del acceso directo de los usuarios |

> Ejemplo de roles: Servidor Web, Servidor de Aplicaciones, Servidor de Base de Datos.

---

## 5. Dise�o conceptual de la arquitectura

### 5.1 Organizaci�n por capas

Describa c�mo se organiza la infraestructura en capas:

- **Capa de Presentaci�n:** Incluye el servidor web, encargado de recibir las solicitudes de los usuarios y presentar la información de forma accesible
- **Capa de Aplicaci�n:** Incluye el servidor de aplicaciones, responsable de procesar las solicitudes, aplicar reglas de negocio y comunicarse con la base de datos
- **Capa de Datos:** Incluye el servidor de Bases de Datos, donde se almacena la información financiera y de

Indique qu� componentes se consideran expuestos y cu�les permanecen en la red interna.

---

## 6. Diagrama l�gico de infraestructura

Diagrama conceptual de la infraestructura.

```mermaid
flowchart TD
    U["Usuarios"]

    subgraph Zona_Publica ["Zona Publica DMZ"]
        A["Servidor Web"]
    end

    subgraph Zona_Privada ["Red Interna"]
        B["Servidor de Aplicaciones"]
        C["Servidor de Base de Datos"]
    end

    subgraph Gestion ["Gestion y Soporte"]
        D["Sistemas de Respaldo"]
        E["Sistema de Monitoreo"]
    end

    U --> A
    A --> B
    B --> C
    C --> D
    B --> E
    C --> E

