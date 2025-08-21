# 📕✍Sistema de Gestión de una Biblioteca
➡Una base de datos para administrar libros, autores y préstamos.
## Objetivos
1. Optimizar el registro y control de libros y usuarios de la biblioteca.
2. Automatizar el préstamo y devolución de materiales para reducir errores y tiempos de espera.
3. Facilitar la búsqueda y consulta de información mediante un catálogo digital.
---
### Tecnologías a usar
- Python
- SQL
- GitHub
---
> [!NOTE]
>#### Cita
>"Un libro es un sueño que tienes en tus manos." — Neil Gaiman"

### Enlace
🎮[Enlace a Juegos](https://www.juegos.com/)

---
### Imagen
[Imagen de Libros](imagen/books.jpg)
---

### Bloque de Codigo
''' python
```python
# Ejemplo simple: gestión mínima de una biblioteca (Python)
from dataclasses import dataclass, field
from typing import Dict, List

@dataclass
class Book:
    id: int
    title: str
    author: str
    available: bool = True

@dataclass
class Library:
    catalog: Dict[int, Book] = field(default_factory=dict)

    def add_book(self, book: Book):
        self.catalog[book.id] = book

    def loan_book(self, book_id: int) -> bool:
        book = self.catalog.get(book_id)
        if book and book.available:
            book.available = False
            return True
        return False

    def return_book(self, book_id: int) -> bool:
        book = self.catalog.get(book_id)
        if book and not book.available:
            book.available = True
            return True
        return False

    def search_by_title(self, q: str) -> List[Book]:
        return [b for b in self.catalog.values() if q.lower() in b.title.lower()]

# Uso mínimo
lib = Library()
lib.add_book(Book(1, "Cien años de soledad", "G. García Márquez"))
print(lib.search_by_title("cien"))
```