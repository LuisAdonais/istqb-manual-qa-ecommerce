
# System Under Test (SUT)

| Atributo      | Detalle                                        |
| :---          | :---                                           |
| **Ubicación** | `00-context-and-overview/system-under-test.md` |
| **Proyecto**  | Tricentis Demo Web Shop                        |
| **Versión**   | 1.2                                            |
| **Fase STLC** | Pre-Planning                                   |
| **Estado**    | ✅ Approved                                    |
| **QA Owner**  | Luis Adonais Malave Gamardo                    |

---

> [!NOTE]
> Este proyecto no contó con documentación funcional previa — es un entorno
> demo público usado para practicar. Construí los **`REQ`** y **`AC`** por
> ingeniería inversa: observé el comportamiento real del SUT y formalicé lo
> que el sistema efectivamente hace. Es una limitación conocida del contexto
> y el punto de partida de todo el ciclo.

---

## Identificación

| Atributo         | Detalle                                       |
| :---             | :---                                          |
| **Nombre**       | Tricentis Demo Web Shop                       |
| **URL**          | <https://demowebshop.tricentis.com/>          |
| **Arquitectura** | Web — Cliente/Servidor                        |
| **Dominio**      | E-commerce B2C                                |
| **Entorno**      | Windows 10 Pro / Firefox 150.0.1 (64-bit)     |

---

## Stakeholders

| Rol             | Acceso Funcional                        |
| :---            | :---                                    |
| Guest User      | Navegación, búsqueda, carrito           |
| Registered User | Login, checkout, historial de órdenes   |

---

## Módulos en Alcance

| Módulo    | Ref. **`REQ`** |
| :---      | :---           |
| Búsqueda  | **`REQ-01`**   |
| Catálogo  | **`REQ-02`**   |
| Producto  | **`REQ-03`**   |
| Carrito   | **`REQ-04`**   |
| Registro  | **`REQ-05`**   |
| Login     | **`REQ-06`**   |
| Checkout  | **`REQ-07`**   |

---

## Fuera de Alcance

- Backend / APIs
- Base de datos (SQL)
- Pagos reales
- Pruebas no funcionales (carga, seguridad, accesibilidad)
